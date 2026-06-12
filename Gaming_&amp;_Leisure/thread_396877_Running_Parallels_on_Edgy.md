---
title: "Running Parallels on Edgy"
date: 2007-03-30
forum: Gaming &amp; Leisure
---

### Post by pwykersotz on 2007-03-30
[B]Hi everyone,

Long story short, I want to run Parallels on Edgy so I can run Windows without the hassle of rebooting.  I'm hoping that games will run decently under it.  (Please correct me now with curses and flames if I'm mistaken)  Even if games aren't supported, I'd still like to do this as an experiment.

Anyway, I grabbed the deb and the tgz file from [http://www.parallels.com/en/download/workstation](http://www.parallels.com/en/download/workstation), and tried the process below with each of them, getting the same results each time.[/B]

root@Jyara[parallels-2.2.2112-lin]$ sh install.sh

Installing Parallels Workstation 2.2 build 2112

[: 16: ==: unexpected operator

Uninstalling Parallels Workstation 2.2

     Uninstalling drivers...
/usr/lib/parallels/autostart/drivers_stop: 21: Syntax error: "(" unexpected
     Deleting files...
Uninstallation has been completed.
     Copying files...
Installation has been completed.

      You should configure Parallels Workstation 2.2
      before starting it for the first time.
      Issue parallels-config command.
root@Jyara[parallels-2.2.2112-lin]$ parallels-config

You must read and accept license agreement to run Parallels Workstation 2.2
To list by pages use Spacebar key.
Press 'ENTER' to continue...


read: 1: arg count
End User License Agreement For Parallels (R) Workstation

Insert License Here...

Do you accept terms of license agreement ? (Y/N)
y

[: 141: ==: unexpected operator
     Compiling Parallels Workstation 2.2 drivers...
     Drivers have been compiled successfully.
/usr/bin/parallels-config: 175: pushd: not found
/usr/bin/parallels-config: 186: popd: not found
     Installing drivers...
     Starting drivers...
/usr/lib/parallels/autostart/drivers_start: 19: Syntax error: "(" unexpected
Parallels Workstation drivers were successfully configured
and compiled but cannot be started (insmod command failed).
Run 'dmesg' command for more information.
exit: 3: Illegal number: -1

[B]Yes, this output starts by uninstalling my previous mistake, but I got the exact same errors the first time too.  It looks like getting pushd and popd up and going are key to this, but my internet searches for doing so have given me nothing.  Any suggestions?

Also, I didn't post the dmesg output because it's rather long and I'm not sure if it's entirely relevant at this point.  If I get a request, I'll do it.[/B]

---

### Post by amohanty on 2007-03-30
> /usr/bin/parallels-config: 175: pushd: not found
/usr/bin/parallels-config: 186: popd: not found
Installing drivers...
Starting drivers...
/usr/lib/parallels/autostart/drivers_start: 19: Syntax error: "(" unexpected
Parallels Workstation drivers were successfully configured

This suggests a couple of things:
1. pushd and popd should pretty much be available. In a terminal try 
pushd /tmp
popd
and post the output.

2. /usr/lib/parallels/autostart/drivers_start - is probably a script. If it is can you post the contents.

Finally after another install attempt post the output of:
dmesg | tail -n 50

AM

---

### Post by pwykersotz on 2007-03-30
**Output of pushd /temp:**
/tmp /home/rayn/Desktop/Parallels/parallels-2.2.2112-lin

**Output of popd:**
/home/rayn/Desktop/Parallels/parallels-2.2.2112-lin

**Here's the script /usr/lib/parallels/autostart/drivers_start:**

#!/bin/sh
#############################################################
# Copyright (C) 2005 Parallels Inc.  All Rights Reserved.
# Load all drivers
#############################################################

. /usr/lib/parallels/gettext.sh

export TEXTDOMAIN="parallels"

version_file=/usr/lib/parallels/parallels-version

mainname="Parallels"
submname="Workstation"
v_maj="`grep 'VER_MAJOR' $version_file | awk '{print $2;}'`"
v_min="`grep 'VER_MINOR' $version_file | awk '{print $2;}'`"
mainver="$v_maj.$v_min"

function modload() {
    modpath=$1
    modname=$2
    moddesc=$3
    moddev=$4
    insalt=$5

    eval_gettext "Loading \$mainname \$submname \$mainver \$moddesc ... "; echo

    if test "`cat /proc/modules | grep -e $modname`"; then
        eval_gettext " \$mainname \$submname \$maniver \$moddesc already loaded."; echo
    else

	module_file_exist=`ls /lib/modules/\`uname -r\`/kernel/drivers/misc/parallels/$modpath.* 2>/dev/null`
		 if [[ "$module_file_exist" == "" ]]; then
            eval_gettext " Error: \$moddesc module is not found in /lib/modules/`uname -r`/kernel/drivers/misc/parallels/
 Perhaps installation or/and configuration was done incorrectly.
 Run \"parallels-config\" again."; echo
		exit -1
        else
            if test -z $insalt; then
                /sbin/modprobe $modpath
            else
                /sbin/modprobe $modpath rsalt=$insalt
            fi
                    
            err=$?
            if test $err -ne 0; then
                eval_gettext " Can not load \$moddesc module."; echo
                exit -1
            fi
        fi
    fi
    
    if test ! -e $moddev; then
        if test ! -c $moddev; then
            minor=`cat /proc/misc | grep $modname | awk '{ print $1 }'`
            if test ! -z $minor; then
                if test -e $moddev; then
                    rm -f $moddev
                fi
                mknod $moddev c 10 $minor 2> /dev/null
            fi
        fi
    fi
}

if test `id -u` -ne 0; then
    eval_gettext "You must be root to run this script.
Now \"su -c \$0\" command will be issued and you will be
prompted for root password."; echo
    su -c $0
    exit $?
fi

case `uname -s` in
    Linux)
        # generate salt
        salt=`head -c 16 /dev/urandom | hexdump | awk '{ print $2$3$4$5$6$7$8$9 }'`
        # save salt
        echo $salt > /usr/lib/parallels/.random_salt
        chmod 400 /usr/lib/parallels/.random_salt

	/sbin/depmod -a
	
	# load hypervisord
	modload "hypervisor" "hypervisor" "hypervisor" "/dev/hypervisor"

	# load vm-main
	modload "vm-main" "vm[_|-]main" "vm-main" "/dev/vm-main" "$salt"

	# load vm-bridge
	modload "vm-bridge" "vm[_|-]bridge" "vm-bridge" "/dev/vm-bridge"

	# load vmvirtualnic
	modload "vmvirtualnic" "vmvirtualnic" "vmvirtualnic"
		
        /usr/lib/parallels/autostart/prl_dhcpd -d vnic0

    ;;
    *)
        gettext "Error: Unknown operating system type."; echo
	exit -1
    ;;
esac
exit 0

**Finally, here's the output of dmesg | tail -n 50:**

root@Jyara[parallels-2.2.2112-lin]$ dmesg | tail -n 50
[17189999.660000] Buffer I/O error on device sdc1, logical block 254910
[17189999.660000] Buffer I/O error on device sdc1, logical block 254910
[17189999.660000] Buffer I/O error on device sdc1, logical block 254910
[17189999.660000] Buffer I/O error on device sdc1, logical block 254911
[17190001.740000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17275422.552000] usb 2-1: USB disconnect, address 4
[17287030.380000] UDF-fs: No VRS found
[17287030.464000] UDF-fs: No VRS found
[17287030.592000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17287030.596000] ISOFS: changing to secondary root
[17289146.248000] UDF-fs: No VRS found
[17289146.388000] UDF-fs: No VRS found
[17289146.528000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17289146.528000] ISOFS: changing to secondary root
[17289336.524000] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[17289336.524000]     Additional sense: Medium not present
[17289336.524000] end_request: I/O error, dev sr0, sector 64
[17289336.524000] printk: 10 messages suppressed.
[17289336.524000] Buffer I/O error on device sr0, logical block 16
[17289336.556000] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[17289336.556000]     Additional sense: Medium not present
[17289336.556000] end_request: I/O error, dev sr0, sector 68
[17289336.556000] Buffer I/O error on device sr0, logical block 17
[17289336.572000] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[17289336.572000]     Additional sense: Medium not present
[17289336.572000] end_request: I/O error, dev sr0, sector 64
[17289336.572000] Buffer I/O error on device sr0, logical block 16
[17289336.572000] Buffer I/O error on device sr0, logical block 17
[17289336.672000] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[17289336.672000]     Additional sense: Medium not present
[17289336.672000] end_request: I/O error, dev sr0, sector 64
[17289336.672000] Buffer I/O error on device sr0, logical block 16
[17289336.672000] Buffer I/O error on device sr0, logical block 17
[17289336.688000] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[17289336.688000]     Additional sense: Medium not present
[17289336.688000] end_request: I/O error, dev sr0, sector 64
[17289336.688000] Buffer I/O error on device sr0, logical block 16
[17289336.688000] Buffer I/O error on device sr0, logical block 17
[17289336.840000] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[17289336.840000]     Additional sense: Medium not present
[17289336.840000] end_request: I/O error, dev sr0, sector 64
[17289336.840000] Buffer I/O error on device sr0, logical block 16
[17289336.840000] Buffer I/O error on device sr0, logical block 17
[17289336.848000] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[17289336.848000]     Additional sense: Medium not present
[17289336.848000] end_request: I/O error, dev sr0, sector 64
[17289362.764000] UDF-fs: No VRS found
[17289362.912000] UDF-fs: No VRS found
[17289363.048000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17289363.048000] ISOFS: changing to secondary root

**To provide some context on this last bit, I have no sdc device on my system, and sr0 is my DVD burner.  Also, both my drives are ext3, so I have no idea what the "FAT" bit is about.**

---

### Post by amohanty on 2007-03-30
> function modload() {

In the script, remove the word 'function' from there. Ubuntu does not have sh, instead it uses dash and symlinks to it.

Also post the output of the dmesg, "after" you run the installer and it fails.

AM

---

### Post by pwykersotz on 2007-03-30
I've removed the "function" bit and retried, but with absolutely no change (I did a character by character search of the output compared to previously and they're identical).

The dmesg output is the same as in my last post, and it is definitely after my fresh install attempt.

---

### Post by amohanty on 2007-03-30
Just wondering why you arent using the deb installer from the site??
AM

---

### Post by pwykersotz on 2007-03-30
It was the first thing I tried.  After it failed, I tried the tgz file.  Both had the same errors, and both still do.  I'm using the tgz file because it was easier to get to by cycling through previous commands than the deb file.

Short answer, convenience.

---

### Post by pwykersotz on 2007-03-30
Resolved, thanks to Alexander Heß on an earlier thread.  Thanks for your help, AM.

---

### Post by derek_harding on 2007-04-01
/bin/sh points to /bin/dash which won't compile, as you found. Change the link to point to /bin/bash and it should compile cleanly.

As root:
rm /bin/sh
ln  -s /bin/bash /bin/sh
   sorted I hope.

Derek

---

### Post by nuklehed on 2007-04-15
Removing 'function' from both /usr/lib/parallels/autostart/drivers_start and /usr/lib/parallels/autostart/drivers_stop worked perfectly for me. I also verified that pushd and popd both had normal output. Thanks AM.

nuklehed

---

