---
title: "Getting grub to boot windows"
date: 2009-06-22
forum: General Help
---

### Post by dazman19 on 2009-06-22
Hi,

I have a somewhat unusual setup.

I have 4 hard drives, 2x 160gb and 2x750gb (these 750gb are just storage)

Ubuntu is installed on /dev/sda1 (160gb) which is my first boot device.
I disconnected all the disks and installed windows on /dev/sdb
I think it is on the second partition on that device so its /dev/sdb2 this is the second 160gb drive.

I want to be able to boot it,
I have tried the following:

title		Windows XP SP3
rootnoverify	(hd1,1)
makeactive	
chainloader	+1

but grub just says: starting up... and it pauses...

I am also concerned that once I am in windows if windows sees another hard drive (sda) will it write a signature to it and destroy grub?


daz@ubuntu:~$ cat /boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd


Here is the output of my fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3d0a3d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18236   146480638+  83  Linux
/dev/sda2           18237       19457     9807682+   5  Extended
/dev/sda5           18237       19457     9807651   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10f3da8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         331     2658726   83  Linux
/dev/sdb2   *         332       19456   153621562+   7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ae58afc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   42  SFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3d0a3d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91202   732574583+  ee  GPT

---

