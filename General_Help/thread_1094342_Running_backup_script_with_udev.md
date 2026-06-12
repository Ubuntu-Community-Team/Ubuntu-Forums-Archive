---
title: "Running backup script with udev"
date: 2009-03-12
forum: General Help
---

### Post by Rackstar on 2009-03-12
Hello,

I have been trying to get my backup script running when I plug my USB dive in.

But it still seems that it refuses to work...

These are my rules: (in /etc/udev/rules.d/10-local.rules)
```
SUBSYSTEM=="block", ATTRS{product}=="Freecom Network Drive", SUBSYSTEMS=="usb", KERNEL=="sd?1", NAME="freecomHD", RUN+="/usr/bin/usb_backup.sh"

```

with /usr/bin/usb_backup.sh
```
#!/bin/bash
/usr/bin/notify-send -t 0 "Backup Message" "Backup device detected, starting backup."
sleep 5
sbackupd
/usr/bin/notify-send -t 0 "Backup Message" "Your USB Backup has completed."

```

The script runs as it should when I manually run it as root.


This is what I get when I do "udevinfo -a -p $(udevinfo -q path -n /dev/sdb)".

```
looking at device '/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host5/target5:0:0/5:0:0:0/block/sdb':
    KERNEL=="sdb"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="976773168"
    ATTR{capability}=="12"
    ATTR{stat}=="     439    30507    32116     2328        0        0        0        0        0     1604     2328"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host5/target5:0:0/5:0:0:0/block':
    KERNELS=="block"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host5/target5:0:0/5:0:0:0':
    KERNELS=="5:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="WDC WD50"
    ATTRS{model}=="00AAVS-00G9B0   "
    ATTRS{rev}=="    "
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x1c5"
    ATTRS{iodone_cnt}=="0x1c5"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host5/target5:0:0':
    KERNELS=="target5:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host5':
    KERNELS=="host5"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0':
    KERNELS=="5-6:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v07ABpFCBFd0000dc00dsc00dp00ic08isc06ip50"
    ATTRS{interface}=="MSC Bulk-Only Transfer"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-6':
    KERNELS=="5-6"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="USB Mass Storage"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{urbnum}=="5170"
    ATTRS{idVendor}=="07ab"
    ATTRS{idProduct}=="fcbf"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="5"
    ATTRS{devnum}=="8"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="0"
    ATTRS{product}=="Freecom Network Drive"
    ATTRS{serial}=="7D5000AA6350"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5':
    KERNELS=="usb5"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{authorized_default}=="1"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="147"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="5"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.27-11-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x27cc"
    ATTRS{subsystem_vendor}=="0x1025"
    ATTRS{subsystem_device}=="0x0107"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00008086d000027CCsv00001025sd00000107bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

Can anybody see the problem?

---

### Post by unutbu on 2009-03-12
I think the udev rule should specify SUBSYSTEMS only once. So perhaps try changing

```
SUBSYSTEM=="block", ATTRS{product}=="Freecom Network Drive", SUBSYSTEMS=="usb", KERNEL=="sd?1", NAME="freecomHD", RUN+="/usr/bin/usb_backup.sh"
```

to
```

ATTRS{product}=="Freecom Network Drive", SUBSYSTEMS=="usb", KERNEL=="sd?1", NAME="freecomHD", RUN+="/usr/bin/usb_backup.sh"


```

---

### Post by Rackstar on 2009-03-12
Hey,

Thanks for the fast reply!

But still nothing happens. (Also one was SUBSYSTEM, other was SUBSYSTEM_S_)

EDIT: the rules this time
```
SUBSYSTEMS=="usb", KERNEL=="sd?1", ATTRS{product}=="Freecom Network Drive", NAME="freecomHD", RUN+="/usr/bin/usb_backup.sh"

```

Thanks. Any other idea?

---

### Post by unutbu on 2009-03-12
Oops, indeed you are right -- SUBSYSTEM and SUBSYSTEMS are different. 
[list]
[*]Did you run
```

sudo udevadm control --reload-rules
```

after changing the udev rule?

[*]It would be nice to know if (A) the script is being run, but quitting early, or (B) the script in never getting run at all.

If we are in case (A), then we can stop fiddling with the udev rule and concentrate on the script.

If (B), then we need to work on the udev rule.

To find out if we are in case (A) or (B), perhaps try this: Edit your script by adding these two lines:
```

#!/bin/bash
[B]env > /tmp/env.out
DISPLAY=:0.0[/B]
/usr/bin/notify-send -t 0 "Backup Message" "Backup device detected, starting backup."
sleep 5
sbackupd
/usr/bin/notify-send -t 0 "Backup Message" "Your USB Backup has completed."

```
Run 
```

sudo udevadm control --reload-rules
```

Unplug and then plug in the drive. See if you get a file called /tmp/env.out.

If you see /tmp/env.out, then we are in case (A). 

If you do not see /tmp/env.out, then we are in case (B).
[/list]

---

### Post by Rackstar on 2009-03-12
Thank you very much for helping me out with this one!

I used ```
sudo /etc/init.d/udev restart
``` to restart it. 

I tried yours but It said:
```

ruben@ruben-laptop:~$ sudo udevadm control --reload-rules
unrecognized command 'reload-rules'

```

Some package missing?

---

### Post by Rackstar on 2009-03-12
For some reason, he does not want to mount the drive anymore? (Gives error dialog box)

The env.out file is there! But no backup

Thanks!

See files:
[http://www.ninetynine.be/screens/76cea3a131608ccc0f503b18846589f8026bd192.png](http://www.ninetynine.be/screens/76cea3a131608ccc0f503b18846589f8026bd192.png)
[http://www.ninetynine.be/screens/c81f9c6b23cfead105e97d660d27091a48d770ec.png](http://www.ninetynine.be/screens/c81f9c6b23cfead105e97d660d27091a48d770ec.png)

Extra details:
[http://www.ninetynine.be/screens/7f9617924476b4cc04358a7915188092a7372bbe.png](http://www.ninetynine.be/screens/7f9617924476b4cc04358a7915188092a7372bbe.png)

(please note that I was able to normally use the HDD in the past. The HDD is formatted into NTFS)

---

### Post by unutbu on 2009-03-12
Did you unmount the drive before unplugging it?
If you think this is the problem, follow taurus's advice here:
[http://ubuntuforums.org/showthread.php?t=1008357](http://ubuntuforums.org/showthread.php?t=1008357)

The more I think about this, the more I suspect udev is not the right tool for this job.

The problem is udev is very low-level. It creates the device file for the device. HAL is a little higher level. It does its work after udev is finished. HAL automounts the USB drive. sbackupd will not work until after the USB drive is mounted. So we probably need to work on setting up a HAL policy, rather than a udev rule. 

Please note that I am not an expert at udev or HAL, so what I said above is largely speculation.

If you agree with the above speculation, I can try to help you write a HAL policy, but it would be new ground for me too, so it may take some time unless a more knowledgable forum reader jumps in.

---

### Post by Rackstar on 2009-03-12
Hey,

I have read something about HAL, but didn't understand it. Also I was suggested udev on this thread: [http://ubuntuforums.org/showthread.php?t=1092617&highlight=backup+mount](http://ubuntuforums.org/showthread.php?t=1092617&highlight=backup+mount) .

I am willing to learn to use HAL. But on one of the screenshots you can see that they suggested to run chkdsk on the HDD on windows. A very strange question to me, but then again, it's in NTFS, so I can understand it.

I'm running that chkdsk first on Windows. But it hangs on about 15% but I know there is one huge file on the disk, so I hope it's just hanging on that file. It seems unsafe to cancel this process. I choose NTFS because I need to access it on Windows too. I know ext3 should have been a better choice.

Thanks for all the trouble! I'm pleasantly suprised of the good help on this forum.

I'll get back to this thread from the moment the chkdsk is finished.

Thanks

---

### Post by Rackstar on 2009-03-12
> **unutbu said:**
> Did you unmount the drive before unplugging it?
If you think this is the problem, follow taurus's advice here:
[http://ubuntuforums.org/showthread.php?t=1008357](http://ubuntuforums.org/showthread.php?t=1008357)



I unplugged it a couple of hundred times today, so I can't garantee you that I unmounted it first every time ;)

---

### Post by Rackstar on 2009-03-12
I used chkdsk on windows, plugged it in, and it asked for a password. I just entered my root password and I could access it. There was recycle bin and a "System volume information" folder created, when I deleted it. It didn't ask a password anymore on plug in.

env.out is still being created. But no messages pop up and no backup is performed.

EDIT: maybe let's try HAL

Thanks!

---

### Post by unutbu on 2009-03-12
Okay, I just did a test and managed to successfully autobackup a directory on to an NTFS partition on a USB flash drive.

This is what I did:

I made a file called```


/etc/udev/rules.d/81-local.rules
```

I used 81 because /etc/udev/rules.d/README says
> 
Files should be named xx-descriptive-name.rules, the xx should be
chosen first according to the following sequence points:

  80   rules that run programs (but do not load modules)


This is the contents of /etc/udev/rules.d/81-local.rules
```

SUBSYSTEM=="block", SUBSYSTEMS=="usb", KERNEL=="sd?1", RUN+="/usr/local/bin/test.sh"
```

and this is the contents of /usr/local/bin/test.sh:
```

#!/bin/sh
mount /dev/sdb1 /mnt
rsync -a /home/user/test/ /mnt/test/
```

One reason why your script was not working is because /dev/sdb1 had not been mounted anywhere at the moment sbackupd was being run. We can use udev, but we need to mount the partition manually first. 

I'm not familiar with how sbackupd works. Are you willing to try rsync? I like rsync.

Also, let's start by making the script as simple as possible -- comment out the notify-send commands.

Good luck with the chkdisk. Once you are done with that, it looks like it should be quite easy to setup autobackup using udev.

Edit: Oh -- I'm very glad you got the drive to work again!

---

### Post by Rackstar on 2009-03-12
Hey,

I need to go now, I'll check the thread again tomorow.

Thanks for all your help.

If anybody else knows what the problem could be, don't hesitate ;)

---

### Post by Rackstar on 2009-03-13
Hey,

Thanks for doing this for me!

I moved my rules to /etc/udev/rules.d/81-local.rules
```
SUBSYSTEMS=="usb", KERNEL=="sd?1", ATTRS{product}=="Freecom Network Drive", NAME="freecomHD", RUN+="/usr/bin/usb_backup.sh"

```

My script:
```
#!/bin/sh  
mount /dev/sdb1 /mnt           
# /usr/bin/notify-send -t 0 "Backup Message" "Backup device detected, starting backup"
# sleep 5
# sbackupd
# /usr/bin/notify-send -t 0 "Backup Message" "Your USB Backup has completed."
env > /mnt/env.out

```

Notice that I changed from bash to sh. Does this change something? (I remember bash from college)

What happens: The drive is still being mounted on /media/FREECOM HDD (where this name comes from, I don't know). And a file is created in /mnt/env.out, but the drive isn't mounted there.

EDIT: The mount failed because I gave the name "freecomHD" to the device in udev. Doing mount /dev/freecomHD fixed it.

> I'm not familiar with how sbackupd works. Are you willing to try rsync? I like rsync.
I would follow you through hell! I just picked out sbackup, because I didn't like timevault. I like the way you can go back in time, but I don't know if that is so usefull.

Nothing ever seems to go according to plan in my world. :)

Thanks!

---

### Post by Rackstar on 2009-03-13
Hey!

The good news is, that it now backups when I plug it in. Which was the main purpose.

Now some annoying little things that show up:

When I plug it in, it shows a media icon in the panel (using gnome). It then backups. And then another usb-device icon appears. The sad part is, I can't unmount the media. I'm only able to unmount it doing

```
sudo umount /media/freecom
```

Which isn't that bad, but I really want this to be perfect :)

Also the notifications don't show. Probably because the script is run by root.

Doing 
```
/usr/bin/notify-send -t 0 "Backup Message" "Backup"
```
works, but doing

```
sudo /usr/bin/notify-send -t 0 "Backup Message" "Backup"
```
doesn't work.

Maybe there is some parameter, I'll have a look around.

Thanks!

---

### Post by unutbu on 2009-03-13
Hey, I think we are making progress! :)

To get notify-send working:

Save this [gnome-hack script]("http://gnome-hacks.org/hacks.html?id=82") 
to /usr/local/bin/alt-notify-send

Make it executable:
```

chmod 755 /usr/local/bin/alt-notify-send
```

Then alter your script to call alt-notify-send like this:
```

su USER alt-notify-send "Backup Message" "Backup" 0
```

Change USER to your username

I've tried this script and got it to work when I plugged in a USB flash drive. 

The reason why notify-send was not working was because notify-send uses the DBUS_SESSION_BUS_ADDRESS environment variable and that variable was not set in the shell that runs your script. This environment variable is set when you start a gnome session, but is not set when root runs a udev rule. 

Moreover, one user can not send messages to another user using notify-send. So we use "su" to change root to your normal user, and we use the alt-notify-send script to find and set the DBUS_SESSION_BUS_ADDRESS before launching notify-send.

To fix the umount problem, please post your script.

---

### Post by Rackstar on 2009-03-13
I also found a variant of this script, but didn't got it working. I tried yours, but it didn't also do a thing.

This is the hack you linked to. I also tried changing whoami to my username, but then it kept saying, ruben: not found.

```
ruben@ruben-laptop:~$ alt-notify-send "test"
/usr/local/bin/alt-notify-send: 2: ruben: not found
pgrep: invalid user name: gnome-session

```

EDIT: Hahaha, Now I get it who-am-i, not that whoami was the username. Sorry :) And the quotes were command substitutions, that's why `ruben` didn't work.

```
#!/bin/sh
user=`whoami`
pids=`pgrep -u $user gnome-session`
title=$1
text=$2
timeout=$3

if [ -z "$title" ]; then
        echo You need to give me a title >&2
        exit 1
fi
if [ -z "$text" ]; then
        text=$title
fi
if [ -z "$timeout" ]; then
        timeout=60000
fi

for pid in $pids; do
        # find DBUS session bus for this session
        DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
                /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
        # use it
        DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS \
        notify-send -u low -t $timeout "$title" "$text"
done

```

If I run this separately, it gives no output, and no popup. 

And this is my script.
```
#!/bin/bash

mount /dev/freecomHD /media/freecom/
su ruben alt-notify-send "Backup Message" "backup" 0                          
sleep 5
# sbackupd
su ruben alt-notify-send "Backup Message" "Your USB Backup has completed." 0

```

We're so close! I really think this will be usefull to other people to. 

Thank you very much for helping me get this far!

EDIT: a little more information about the unmount bug:
[http://www.ninetynine.be/screens/e73b5766fa124cf928aac17e1f31bfdf4236e3f3.png](http://www.ninetynine.be/screens/e73b5766fa124cf928aac17e1f31bfdf4236e3f3.png) 
It's in dutch, it says: "Could not unmount, the device was probably mounted manually in terminal". Rest is in english.

---

### Post by unutbu on 2009-03-13
After getting the "Could not unmount" error window, go to the terminal and type
```

mount
```

please post the output.

Now, regarding alt-notify-send: what is the output of these two commands when run from the terminal:
```

ps axuw | grep gnome-session
pgrep gnome-session
```

---

### Post by Rackstar on 2009-03-13
Not always getting error message, sometimes it just does nothing, like now.

Got two icons on my gnome panel.
-------------------
| usb device icon |
-------------------
options: 
mount FREECOM HDD

--------------
| drive icon |
--------------
options: 
Open freecom
unmount freecom

Except Open, all of the options don't do anything.

mount output:
```
ruben@ruben-laptop:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda4 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ruben/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ruben)
/dev/freecomHD on /media/freecom type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

First command:
```
ruben@ruben-laptop:~$ ps axuw | grep gnome-session
ruben     5818  0.0  0.1  14172  3748 ?        S    14:33   0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
ruben     7249  0.0  0.0   3256   816 pts/0    S+   14:52   0:00 grep gnome-session

```

Second command:
```
ruben@ruben-laptop:~$ pgrep gnome-session
ruben@ruben-laptop:~$ 

```

The second command didn't output anything, so probably there's something wrong here.

EDIT: sorry, got to go, will be back in about 2 hours.

---

### Post by unutbu on 2009-03-13
> The second command didn't output anything, so probably there's something wrong here.

Yes. This is why alt-notify-send is not working. 

Since you are running a gnome-panel, let's try this: 

Edit /usr/bin/local/alt-notify-send by changing
```

pids=`pgrep -u $user gnome-session`
```

to 
```

pids=`pgrep -u $user gnome-panel`
```

If that does not work, please post the output of 
```

pstree
```

Regarding the umount problem: let's try adding this line to the end of the backup script:
```

umount /dev/freecomHD
```

---

### Post by Rackstar on 2009-03-13
Haha!

I could kiss you!

Everything works!

It has a very handy side-effect. When plugging in the drive icon appears on my gnome-panel, and I still can't unmount it using the button "Unmount", but probably only in terminal.

But because of adding "umount /dev/freecomHD" to the script, the drive icon disappears, and the usb-device icon appears, which I can unmount.

So basically, I can't unmount it while doing the backup, which is good :)

Yesssss, backupping never has been so much fun. 

For reference:
/etc/udev/rules.d/81-local.rules:
```
SUBSYSTEMS=="usb", KERNEL=="sd?1", ATTRS{product}=="Freecom Network Drive", NAME="freecomHD", RUN+="/usr/bin/usb_backup.sh"

```

/usr/bin/usb_backup.sh
```
#!/bin/bash

mount /dev/freecomHD /media/freecom/
su ruben alt-notify-send "Backup Message" "USB Backup device detected" 0
sleep 5
sbackupd
su ruben alt-notify-send "Backup Message" "Your USB Backup is completed." 0
umount /dev/freecomHD

```

/usr/local/bin/alt-notify-send
```
#!/bin/sh
user=`whoami`
pids=`pgrep -u $user gnome-panel`
title=$1
text=$2
timeout=$3

if [ -z "$title" ]; then
        echo You need to give me a title >&2
        exit 1
fi
if [ -z "$text" ]; then
        text=$title
fi
if [ -z "$timeout" ]; then
        timeout=60000
fi

for pid in $pids; do
        # find DBUS session bus for this session
        DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
                /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
        # use it
        DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS \
        notify-send -u low -t $timeout "$title" "$text"
done

```

Thanks!

This makes this thread solved, I guess.

---

### Post by Rackstar on 2009-03-13
Stupid question but: How do I mark this thread as solved? :)

---

### Post by unutbu on 2009-03-13
Fantastic. So happy to hear the udev backup script is working to your liking :)

Don't worry about marking the thread Solved; that feature has been disabled for the sake of server stability: [http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

### Post by Rackstar on 2009-03-13
Hey,

I was thinking about the unmount problem, maybe there is a more elegant way.

The idea is: enter a line into /etc/fstab about mounting the device, use udev to run the script **in background** using "&". and include a sleep of 10 seconds in the script, so that the drive had had enough time to mount.

Result: drive get mounted, and backup in background, drive immediately ready to use.

But I tried entering a line into fstab, and on pluggin in I got: "only root can mount", which was a suprise to me, because this thread suggests it:
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

Is this idea an option, or a no go?
Pretty happy how the situation is now, but still a little messy.

Thanks in advance.

---

### Post by unutbu on 2009-03-13
Hm. Your idea sounds interesting and reasonable... Though if we are going to wait for HAL to mount the device, then perhaps executing the script via a HAL policy rather than udev is a better idea after all :) 

Regarding the "only root can mount" error... Please post your /etc/fstab. At the moment I don't know the answer, but we shall figure it out, yes?

---

### Post by Rackstar on 2009-03-13
Hi!

I really like the way you think. Unfortunally I'll be gone this weekend. I switched to rsync (because sbackup was taking way too much space). And now I'm running it, so the backup will take a lot of time.

Is it ok, that I'll come back to it after the weekend? Just letting you know, I really appreciate your help, and not that you would think I just stopped replying.

See you later. ;)

---

### Post by Rackstar on 2009-03-13
Bad news:

If the backup takes more than a couple of minutes. Then no usb-device icon appears after the backup. 

There should be another solution. But I could not find a lot about HAL on the internet.

I will get back to you, after the weekend.

Thanks!

---

### Post by Rackstar on 2009-03-16
Hi there, I'm back.

This is the error I get:
[http://www.ninetynine.be/screens/348c0c193a83e4102359910eacf1f2b70714589f.png](http://www.ninetynine.be/screens/348c0c193a83e4102359910eacf1f2b70714589f.png)
In english: "Only root can mount ..."

This is my fstab.
```
/dev/freecomHD  /media/freecom/         ntfs-3g defaults 0 0
```

Or if you would want to try with HAL, it's ok with me, but I really haven't got a clue how that works..

Thanks in advance!

---

### Post by unutbu on 2009-03-16
Hi Rackstar,
   It is fortunate that you went away for the weekend -- it gave me some time to research this problem. My idea to use HAL policy files seems to be a mistake. After much searching, it seems there is no way to tell HAL to run a script when a USB drive is plugged in. There is a way to do it with dbus (I have a working script!) but it is no easier than using udev, so let's see if we can make udev work first.

Let's try this:

Edit /usr/bin/usb_backup.sh:```


#!/bin/bash
/usr/bin/usb_backup_main.sh &
```

Next, save in /usr/bin/usb_backup_main.sh:
```

#!/bin/bash
mount_point=$(grep freecomHD /etc/mtab)
attempts=1
while [ -z $mount_point ] && [ "$attempts" -le 50 ]; do
    # $mount_point has not been found
    # quit if this fails more than 50 times. 
    # This should not be necessary, but it better to be safe
    # than have the script trapped in this loop forever for
    # some unforeseen reason.
    sleep 1
    mount_point=$(grep freecomHD /etc/mtab)
    attempts=$(($attempts+1))
done

if [ -n "$mount_point" ]; then
    su ruben alt-notify-send "Backup Message" "USB Backup device detected" 0
    sbackupd
    su ruben alt-notify-send "Backup Message" "Your USB Backup is completed." 0
fi
```

Make /usr/bin/usb_backup_main.sh executable:
```

sudo chmod 755 /usr/bin/usb_backup_main.sh
```


When udev detects your USB drive, /usr/bin/usb_backup.sh is run.
usb_backup.sh launches usb_backup_main.sh in the background, and then ends quickly. It is important that usb_backup.sh finishes quickly, since HAL does not automount the partitions until usb_backup.sh ends.

Meanwhile, usb_backup_main.sh is running in the background, checking to see if /dev/freecomHD has been mounted. When it detects that /dev/freecomHD has been mounted, it does the backup. 

I've run a modified version of this setup on my machine and managed to get it to work.

---

### Post by Rackstar on 2009-03-16
Wow, thank you for doing all this effort! 

I believe you have a little syntax error in your code:
```

mount_point=$(grep freecomHD /etc/mtab')

```
shouldn't it be:

```

mount_point=$(grep freecomHD '/etc/mtab')

```
?

(Otherwise I get an error of missing ")")

But I still get error:
```

ruben@ruben-laptop:~$ sudo usb_backup_main.sh 
/usr/bin/usb_backup_main.sh: line 4: [: te veel argumenten

```

Which means: "Too much arguments"

This is my code:
```

#!/bin/bash
mount_point=$(grep freecomHD /etc/mtab)
attempts=1
while [ -z $mount_point ] && [ "$attempts" -le 50 ]; do
    # $mount_point has not been found
    # quit if this fails more than 50 times.
    # This should not be necessary, but it better to be safe
    # than have the script trapped in this loop forever for
    # some unforeseen reason.
    sleep 1
    mount_point=$(grep freecomHD '/etc/mtab')
    attempts=$(($attempts+1))
done

if [ -n "$mount_point" ]; then
        su ruben alt-notify-send "Backup Message" "USB Backup device detected" 0
        # backup little files

        # rsync -a --delete --exclude-from="/home/ruben/backup_exclude.txt"  /h$

        # sync documents
        # rsync -a --delete /home/ruben/Documenten/ /media/freecom/Documenten/

        # rsync music
        # rsync -a --delete /home/ruben/Muziek/ /media/freecom/Muziek/

        # rsync photos
        # rsync -a  /home/ruben/Afbeeldingen/ /media/freecom/Foto\'s/
        # rsync -a  /media/freecom/Foto\'s/ /home/ruben/Afbeeldingen

        su ruben alt-notify-send "Backup Message" "Your USB Backup has complete$
fi

```

But it does seem to execute the code... I'll get back to you shortly

EDIT: note that I'm using rsync now ;) And that I did not set the paths right yet. In the next post I tried with the right paths.

---

### Post by Rackstar on 2009-03-16
Hehe,

It does the trick!

But it still says this if I try to do the command manually:
```

ruben@ruben-laptop:~$ sudo usb_backup_main.sh 
/usr/bin/usb_backup_main.sh: line 4: [: te veel argumenten

```
Again, this means "Too much arguments"

This is the if condition. I remember having this error a lot in college with the test command (or with the brackets [])

But this seems to be a hell of an improvement. No ugly fixes no more, no troubles, only the one error, of which I'm a little afraid that it might cause not to do those different attempts...

Thanks! Really really thanks, this is better help than I could ever imagine.

---

### Post by unutbu on 2009-03-16
Hi Rackstar,
Indeed, I had a dangling apostrophe in the script. I see you fixed it by adding single quotes around /etc/mtab. This is fine, though it is also fine to just remove the single quotes from both sides.

I think the error on line 4 is caused by my forgetting to put $mount_point in quotes.
When you forget the quotes, bash interprets space-separated words in the string as separate arguments. Hence, too many arguments to the [ (test) operator. When you put $mount_point in quotes, then the whole thing is regarded as one string.

Also, one more improvement: Thanks to geirha ([http://ubuntuforums.org/showthread.php?p=6907640#post6907640](http://ubuntuforums.org/showthread.php?p=6907640#post6907640)), we can reach our goal with one usb_backup.sh script instead of two scripts. 

Try placing this in /usr/local/bin/usb_backup.sh, and delete usb_backup_main.sh.

```
#!/bin/bash
**{**
mount_point=$(grep freecomHD /etc/mtab)
attempts=1
while [ -z **"$mount_point"** ] && [ "$attempts" -le 50 ]; do
    # $mount_point has not been found
    # quit if this fails more than 50 times. 
    # This should not be necessary, but it better to be safe
    # than have the script trapped in this loop forever for
    # some unforeseen reason.
    sleep 1
    mount_point=$(grep freecomHD **/etc/mtab**)
    attempts=$(($attempts+1))
done

if [ -n "$mount_point" ]; then
    su ruben alt-notify-send "Backup Message" "USB Backup device detected" 0

    # **Insert rsync commands here**

    su ruben alt-notify-send "Backup Message" "Your USB Backup has completed" 0
fi
**} &**

```

---

### Post by Rackstar on 2009-03-17
Yep,

You were right about the [test] commando, It came back to me, as soon as I started reading your post!

This is it. A very clean solution! And really really fast if you tweak the rsync right. (Which was very easy actually, thumbs up!)

I really think this will be usefull for many people.

And three times hooray for Unutbu. Never knew that backupping could give me so much joy :)

---

### Post by Rackstar on 2009-03-25
Made a blogpost about this:
[http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/)

---

### Post by unutbu on 2009-03-25
Wow, very nice write up! Thank you for taking the time to do this. Contributions like this makes Linux better and better. :)

---

### Post by mihaicj on 2009-05-08
This type of command doesn't work for me:```
su ruben alt-notify-send "Backup Message" "Your USB Backup has completed" 0
```
Instead, I use ```
su -c 'alt-notify-send "Backup Message" "Your USB Backup has completed" 0' myusername
```
This works well from the terminal but not from the script. Any ideas why?

---

### Post by unutbu on 2009-05-08
Is your setup exactly like the one described in [http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/?](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/?)

If not, how does yours differ?

---

### Post by Rackstar on 2009-05-09
Mihaicj, has your problem been solved about the script 'firing 14 times', that you posted on my blog?

We can offer you some help if you want to.

---

### Post by AZzKikR on 2009-06-15
> **Rackstar said:**
> Mihaicj, has your problem been solved about the script 'firing 14 times', that you posted on my blog?

We can offer you some help if you want to.

Hmm I just started a thread explaining the same problem. 

My udev rule works fine, my script gets executed perfectly, albeit 14 times or so. I am not sure how this is happening, but I really don't want my USB stick to get backed up 14 times :D

Any ideas?

---

### Post by OlyPerson on 2010-07-30
Sorry to bring this thread back from the grave but I was going to post a question with the exact same topic.


I am also wanting to run a backup script that runs every time a USB drive is connected but it appears that my udev rules just aren't working and I can't for the life of me figure out how.

I've tried a large number of rules but none seem to work.  Here's my current trial:
```
SUBSYSTEMS=="usb", ATTRS="02AD00000003Ad", RUN+="/usr/lib/myscript.sh"
```
I know my script works as I can run it from the command line and it works just fine and I've fiddled with permissions so that doesn't seem to be an issue either.

So can anyone help me with the udev rules?

EDIT:  Here's my output from "udevadm info -a -p $(udevadm info -q path -n /dev/sdb)"
```

udevadm info -a -p $(udevadm info -q path -n /dev/sdb)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/host6/target6:0:0/6:0:0:0/block/sdb':
    KERNEL=="sdb"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="1"
    ATTR{ro}=="0"
    ATTR{size}=="0"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="53"
    ATTR{stat}=="     106      276      781      224        2        0        2        0        0      212      224"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/host6/target6:0:0/6:0:0:0':
    KERNELS=="6:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="Pretec  "
    ATTRS{model}=="256MB Tiny      "
    ATTRS{rev}=="1.20"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x1bc"
    ATTRS{iodone_cnt}=="0x1bc"
    ATTRS{ioerr_cnt}=="0x123"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/host6/target6:0:0':
    KERNELS=="target6:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/host6':
    KERNELS=="host6"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0':
    KERNELS=="1-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="03"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v4146pBA01d0100dc00dsc00dp00ic08isc06ip50"
    ATTRS{supports_autosuspend}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1':
    KERNELS=="1-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}==" 98mA"
    ATTRS{urbnum}=="1926"
    ATTRS{idVendor}=="4146"
    ATTRS{idProduct}=="ba01"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="3"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{product}=="USB Mass Storage Device"
    ATTRS{serial}=="02AD00000003AD"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="50"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.32-24-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x27cc"
    ATTRS{subsystem_vendor}=="0x17aa"
    ATTRS{subsystem_device}=="0x380b"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d000027CCsv000017AAsd0000380Bbc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by Tarquinn on 2010-08-27
> I've tried a large number of rules but none seem to work. Here's my current trial:
Code:
SUBSYSTEMS=="usb", ATTRS="02AD00000003Ad", RUN+="/usr/lib/myscript.sh"

Why don't you use ATTRS{serial} instead of ATTRS?
If it will not help, try to delete ATTRS attribute. AFAIK this rule will trigger every usb device.

---

### Post by Tarquinn on 2010-08-27
**Important!** Don't forget to specify ACTION=="add" key! Otherwise, your script will start both on device plugging and unmounting.

---

