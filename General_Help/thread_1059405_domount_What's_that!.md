---
title: "domount? What's that?!?"
date: 2009-02-03
forum: General Help
---

### Post by domoso on 2009-02-03
I'm trying to work through USB passthrough for VirtualBox as instructed here:

[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

The instructions I'm stuck on are:

> 
#
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb



You'll notice a reference to domount in the quoted text. I have no idea what this is. I've searched the entire system and have not found a single file named "domount". I've searched google and only found a very few fleeting, not helpful, references to "domount". 

Any assistance to help me understand is appreciated, thanks.

---

### Post by snova on 2009-02-03
It's a function defined in **/lib/init/mount-functions.sh**.

---

### Post by domoso on 2009-02-04
Would this be indicating that it is not working? 

> 
desktop:/dev/bus/usb/001$ sudo /etc/init.d/mountdevsubfs.sh start
/etc/init.d/mountdevsubfs.sh: 20: domount: not found
ln: creating symbolic link `/dev/bus/usb/devices': File exists


---

### Post by snova on 2009-02-04
Odd. This line here (line 28 of mountdevsubfs.sh) should have made it available:

[PHP]. /lib/init/mount-functions.sh[/PHP]

The surrounding code:

[PHP]
PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
[/PHP]

Is yours different?

---

### Post by domoso on 2009-02-04
> 
#
# Functions used by several mount* scripts in initscripts package
#
# Sourcer must set PATH and include /lib/init in it because
# domount() uses the custom readlink program
#
# Sourcer must also source /lib/lsb/init-functions.sh

# $1: directory
is_empty_dir() {
	for FILE in $1/* $1/.*
	do
		case "$FILE" in
		  "$1/.*") return 0 ;;
		  "$1/*"|"$1/."|"$1/..") continue ;;
		  *) return 1 ;;
		esac
	done
	return 0
}


selinux_enabled () {
	which selinuxenabled >/dev/null 2>&1 && selinuxenabled
}


# Called before mtab is writable to mount kernel and device file systems.
# $1: file system type
# $2: alternative file system type (or empty string if none)
# $3: mount point
# $4: mount device name
# $5... : extra mount program options
domount () {
	MTPT="$3"
	KERNEL="$(uname -s)"
	# Figure out filesystem type
	FSTYPE=
	if [ "$1" = proc ]
	then
		case "$KERNEL" in
			Linux|GNU) FSTYPE=proc ;;
			*FreeBSD)  FSTYPE=linprocfs ;;
			*)         FSTYPE=procfs ;;
		esac
	elif [ "$1" = tmpfs ]
	then # always accept tmpfs, to mount /lib/init/rw before /proc
		FSTYPE=$1
	elif [ "$1" = spufs ]
	then # spufs is only relevant on Cell so may be compiled as a kernel module
		if grep -E -qs "spufs\$" /proc/filesystems || modprobe -Q spufs
		then
			FSTYPE=$1
		fi
	elif grep -E -qs "$1\$" /proc/filesystems
	then
		FSTYPE=$1
	elif grep -E -qs "$2\$" /proc/filesystems
	then
		FSTYPE=$2
	fi

	if [ ! "$FSTYPE" ]
	then
		if [ "$2" ]
		then
			log_warning_msg "Filesystem types '$1' and '$2' are not supported. Skipping mount."
		else
			log_warning_msg "Filesystem type '$1' is not supported. Skipping mount."
		fi
		return
	fi

	# We give file system type as device name if not specified as
	# an argument
	if [ "$4" ] ; then
	    DEVNAME=$4
	else
	    DEVNAME=$FSTYPE
	fi

	# Get the options from /etc/fstab.
	OPTS=
	if [ -f /etc/fstab ]
	then
		exec 9<&0 </etc/fstab

		while read TAB_DEV TAB_MTPT TAB_FSTYPE TAB_OPTS TAB_REST
		do
			case "$TAB_DEV" in (""|\#*) continue ;; esac
			[ "$MTPT" = "$TAB_MTPT" ] || continue
			[ "$FSTYPE" = "$TAB_FSTYPE" ] || continue
			case "$TAB_OPTS" in
			  noauto|*,noauto|noauto,*|*,noauto,*)
				exec 0<&9 9<&-
				return
				;;
			  ?*)
				OPTS="-o$TAB_OPTS"
				;;
			esac
			break
		done

		exec 0<&9 9<&-
	fi

	if [ ! -d "$MTPT" ]
	then
		log_warning_msg "Mount point '$MTPT' does not exist. Skipping mount."
		return
	fi

	if mountpoint -q "$MTPT"
	then
		return # Already mounted
	fi

	if [ "$VERBOSE" != "no" ]; then
		is_empty_dir "$MTPT" >/dev/null 2>&1 || log_warning_msg "Files under mount point '$MTPT' will be hidden."
	fi
	mount -n -t $FSTYPE $5 $OPTS $DEVNAME $MTPT
}

#
# Preserve /var/run and /var/lock mountpoints
#
pre_mountall ()
{
	# We may end up mounting something over top of /var, either directly
	# or because /var is a symlink to something that's mounted.  So keep
	# copies of the /var/run and /var/lock mounts elsewhere on the root
	# filesystem so they can be moved back.
	if [ yes = "$RAMRUN" ] ; then
		mkdir /lib/init/rw/var.run
		mount -n --bind /var/run /lib/init/rw/var.run
	fi
	if [ yes = "$RAMLOCK" ] ; then
		mkdir /lib/init/rw/var.lock
		mount -n --bind /var/lock /lib/init/rw/var.lock
	fi
}

#
# Restore /var/run and /var/lock mountpoints if something was mounted
# as /var/.  Avoid mounting them back over themselves if nothing was
# mounted as /var/ by checking if /var/run/ and /var/lock/ are still
# mount points.  Enabling RAMRUN and RAMLOCK while listing /var/run or
# /var/lock in /etc/fstab is not supported.
#
post_mountall ()
{
	if [ yes = "$RAMRUN" ] ; then
		[ -d /var/run ] || mkdir /var/run
		if mountpoint -q /var/run ; then
			umount /lib/init/rw/var.run
		else
			mount -n --move /lib/init/rw/var.run /var/run
		fi
		rmdir /lib/init/rw/var.run
	fi
	if [ yes = "$RAMLOCK" ] ; then
		[ -d /var/lock ] || mkdir /var/lock
		if mountpoint -q /var/lock ; then
			umount /lib/init/rw/var.lock
		else
			mount -n --move /lib/init/rw/var.lock /var/lock
		fi
		rmdir /lib/init/rw/var.lock
	fi
}



It appears so.

---

### Post by snova on 2009-02-04
First of all, [noparse][code][/noparse] tags preserve the indentation, which is particularly helpful for code. ;)

Secondly, that looks like mine for the most part (I'm not doing a line-by-line comparison, though).

But I'm not interested in this file- it contains the function as it should. What about the top of **/etc/init.d/mountdevsubfs.sh**? Check for the previously mentioned line.

---

### Post by domoso on 2009-02-06
Edit: I just reread the thread and realized what you were talking about in post #4. I did not put the new code at the end. I put it at the beginning of the mountdevsubfs.sh script.

>  -desktop:/etc/init.d$ sudo ./mountdevsubfs.sh start
ln: creating symbolic link `/dev/bus/usb/devices': File exists


It appears to be working. Thanks. Don't laugh :) I'm not a coder.

---

### Post by fidsteve on 2009-07-28
It should be noted that the instructions have changed for installations in Intrepid and after.

The lines to be added are similar to the ones that need to be commented out, only there is a small change that prevents the original "commented out" lines to work properly in the newer distro releases.


```
#
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb
```

NOTE: the domount has an additional parameter in the 4th position.

This was found [VirtualBOX ]("https://help.ubuntu.com/community/VirtualBox/USB")page, but does apply to other USB-serial configurations.

---

### Post by berlichman on 2009-09-14
Well, after all has been said, what do I do to make the domount command work.  Thanks.

Bruce

---

