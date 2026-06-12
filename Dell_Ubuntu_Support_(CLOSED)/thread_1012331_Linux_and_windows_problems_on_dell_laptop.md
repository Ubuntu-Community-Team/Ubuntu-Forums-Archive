---
title: "Linux and windows problems on dell laptop"
date: 2008-12-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MikeyUbun2 on 2008-12-15
I am lending a friend of mine my laptop over the Christmas break but they don't know how to use Linux so I said I would install Windows for them temporarily.
I have a new Dell Inspiron 1525 that came pre-installed with Ubuntu 8.04 (i have upgraded to 8.10 though)
When I tried to install windows (using an old disc that i had for my other computer i threw out a few years back so it is all legal) it sed that there was no hard drive detected! and my computer has a hard drive or i wouldn't be typing this rite now! so i tried that windows clone reactOS and it sed the same thing.
I have no idea what the problem is but it could be the format of the hard drive maybe?

---

### Post by falcon61102 on 2008-12-15
More than likely the problem is that Windows does not recognize your HD because it is partitioned in Ex3 format for Ubuntu.  What you can try doing is using a LiveCD to partition a portion of your HD and format it to Fat32, then try the WinXP install.

A side note:  Windows does not like being the second OS on the drive and may give you some problems.  If you still run into problems installing even after partitioning your drive, your best bet would be to either move your Ubuntu partition to the rear of the drive or doing a fresh install with WinXP first.

Post if you run into any issues or have further questions.

---

### Post by tuxxy on 2008-12-15
If its a SATA drive i think old XP discs dont have the driver to read from them aswell

---

### Post by MikeyUbun2 on 2008-12-16
if i boot up the live cd of ubuntu and go to the filesystem it only shows the contents of the live cd. is there a different way to format it? Also, is fat32 compatible with both, or will i have to wipe my linux partition?

---

### Post by armandh on 2008-12-17
I had no end of trouble dual booting XP and Dell 8.04 
XP likes the primary active partition to its self. 

the dell "return to factory specs" disk does not "load" Ubuntu rather It copies an instillation to the HDD as a primary active partition

first: back up what you need to save. all else will be gone.

the easiest and what worked for me was using "parted magic" a live disk partitioner dividing the mini9 flash HDD to a ntfs partition and unpartitioned space.

install the XP to the NTFS partition and then install non dell 8.10 and, at the partition question, select "largest unpartitioned space"

this puts Ubuntu [ext3] and a swap partition in an extended partition after the NTFS. the grub installs A-OK

then restore backed up files.

PS it took me all of 20 minutes to become a gnome GUI user.
the above is an all day project the second time even if you saved the dell driver disk [for the xp]. the only reason I did it is that I wanted a copy quickbooks to be portable.

PPS not being able to load xp is a good excuse not to loan the laptop. in the late 1960s I loaned a car to someone and got it back with a dent in the door and [unknown at the time] a parking citation. I am older and wiser.

---

### Post by MikeyUbun2 on 2008-12-18
i used gparted and i booted it from a usb key and formatted to ntfs but it still couldn't detect a hard disk. i will try parted magic though to see maybe if that makes a difference.

---

### Post by outlaws42 on 2008-12-18
Could you install windows via virtual box. Being that you only need Windows on it to loan to someone. You could show them what icon to click to start virtual box. You could even have VB start in full screen mode so it would look like a Windows machine. 

I don't know just a thought.
Troy

---

### Post by MikeyUbun2 on 2008-12-18
I could not get parted magic to work for some reason but virtualbox sounds like a way better way to do it so i guess i will reinstall ubuntu and see if it works!

---

### Post by MikeyUbun2 on 2008-12-18
Ok so i tried virtual box and it worked waaay better then i expected!:D:D:D
the only problem is my wireless and my sound doesn't work and i need an activation code in 30 days. (my god windows sucks!) but i am not even lending it for 30 days so it should be fine! i hope he's fine with no sound!
but if anyone could help that would be great.

[EDIT]
I got sound and wireless working but internet explorer is a piece of crap and keeps crashing when i start it up. i still need to figure out the usb settings and i think i can get a crack for the activaton code and i am getting firefox via lan

[EDIT AGAIN]
i got everything except usb working!

---

### Post by outlaws42 on 2008-12-19
check this out about virtualbox and usb
[http://www.virtualbox.org/wiki/User_FAQ]("http://www.virtualbox.org/wiki/User_FAQ")

---

### Post by MikeyUbun2 on 2008-12-19
i tried it but i cant do the second line because there is no bash command domount it keeps saying
**I TYPE:**
$ domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
**OUTPUT:**
bash: domount: command not found

How do i add domount to the commands?

---

### Post by upchucky on 2008-12-19
google xp activation hack there are several that will disable the 30 day activation, i have done it on a laptop that i put xp on when i installed ubuntu instead of xp on a second laptop

---

### Post by treggmo on 2008-12-20
MikeyUbun2,
It looks like you forgot the spaces after the commas in the command. Try copying the command and then pasting it in your terminal (right click in the terminal > paste)

---

### Post by outlaws42 on 2008-12-20
you want to put this code 
```
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

```

at the bottom of the 
```
do_start () { 
```
section of your /etc/init.d/mountdevsubfs.sh file.

**note** if you are using any older version of ubuntu the code is already there all you have to do is uncomment it

I will put my mountdevsubfs.sh bellow with the code in bold that you have to add. 
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs
# Required-Start:    mountkernfs
# Required-Stop:
# Should-Start:      udev
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO
#
# This script gets called multiple times during boot
#

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
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

	#
	# Mount /dev/pts. Master ptmx node is already created by udev.
	#
        domount devpts "" /dev/pts devpts   -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
	
	#
	# Magic to make /proc/bus/usb work
	#
	[B]mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb[/B]
}

case "$1" in
  "")
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
	do_start
	;;
  start)
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountdevsubfs [start|stop]" >&2
	exit 3
	;;
esac


```

---

