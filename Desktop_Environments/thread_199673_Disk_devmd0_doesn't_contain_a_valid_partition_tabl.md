---
title: "Disk /dev/md0 doesn't contain a valid partition table"
date: 2006-06-19
forum: Desktop Environments
---

### Post by mike55 on 2006-06-19
Hi, I've just installed Dapper 6.06 and am getting the message shown in the subject when I type fdisk -l. Everything runs fine, but I'm curious about whether this is something I should worry about. I've seen other posts on the web and in other forums about similar messages, but in those cases the problem is usually something like the filesystem not being created.

The system is a fresh install, and the raid configuration, partition layout and diskmounts are as below:

~$ cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sda3[0] sdb3[1]
      144078848 blocks [2/2] [UU]

unused devices: <none>

~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        1520     2441880   82  Linux swap / Solaris
/dev/sda3            1521       19457   144078952+  fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+  83  Linux
/dev/sdb2            1217        1520     2441880   82  Linux swap / Solaris
/dev/sdb3            1521       19457   144078952+  fd  Linux raid autodetect

Disk /dev/md0: 147.5 GB, 147536740352 bytes
2 heads, 4 sectors/track, 36019712 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-25-k7/volatile type tmpfs (rw)
/dev/md0 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

When I type fdisk /dev/md0, I get:
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 36019712.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help):


Any thoughts would be much appreciated.

---

### Post by mike55 on 2006-06-20
Never mind, from reading the top of this page:
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-11.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-11.html)

I believe this is normal behaviour.

Thanks anyway.

---

