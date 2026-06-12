---
title: "USB drive"
date: 2010-03-22
forum: Desktop Environments
---

### Post by gcpennington on 2010-03-22
I removed a USB drive without unmounting.  Now  I can't remove the device in the file browser.  After looking at some posts I am including the following information.  

I believe the offender is /dev/sda3           19275       19457     1469947+  1b  Hidden W95 FAT32

:~$ lsusb
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 174f:1403  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

:~$ mount
/dev/sda2 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-lpia/volatile type tmpfs (rw)
gvfs-fuse-daemon on /home/carl/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=carl)


~$ sudo fdisk -l
[sudo] password for carl: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       24066   de  Dell Utility
/dev/sda2   *           4       19274   154794307+  83  Linux
/dev/sda3           19275       19457     1469947+  1b  Hidden W95 FAT32

Release 8.04 (hardy)
Kernal Linux8.04 
GNOME 2.22.3

Thanks

---

### Post by ajgreeny on 2010-03-22
sda would normally be your internal hard disk, so before you do anything, make sure you are dealing with the correct partition/disk.

What size is the usb disk you are having the problem with?  sda is 160GB, and has a linux install on it on sda2 and no swap.

If this really is the usb disk, and it's the fat32 partition with the problem, try attaching it to a windows computer, as this may be able to mount it and even do the required chkdisk, or whatever it is called in windows, to put things right again.

---

### Post by gcpennington on 2010-03-22
The external USB is 2 GB.  I did put it in a windows box and was told it was unformated, so I formatted Fat32.

---

### Post by ajgreeny on 2010-03-23
So is your problem solved?

---

### Post by sixdrift on 2010-03-23
In the future, should this happen again, plug in the flash drive and run (g)parted to see what it thought about things. Also, check your syslog/dmesg trail to see what it thinks.

I had something like this happen before and the problem was the partition got smacked and it even lost its label. I managed to reformat it to fat32 in gparted and get it going again.

There really is no need to go to Windows for this sort of thing.

---

### Post by gcpennington on 2010-03-23
I reloaded the complete system and its still their.  I strongly suspect, as earlier stated by sixdrift that its a partition.  A little coaching on how to use GPARTED to get rid of it would help.  I would also like to reallocate the unused disk space to ubuntu.

thanks all for the help.

---

### Post by ajgreeny on 2010-03-23
So are you now asking about your ubuntu hard disk install or still the 2GB usb disk?

I'm afraid I am totally confused about what it is you want from us, or where this unused space is.

---

