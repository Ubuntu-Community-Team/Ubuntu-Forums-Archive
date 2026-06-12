---
title: "Trying to mount hard drive nearly there!!"
date: 2006-02-18
forum: Desktop Environments
---

### Post by ade234uk on 2006-02-18
I am trying to mount my second hard drive that is a Windows Drive fat 32 in the terminal

**I first create the mount point in the folder media **
sudo mkdir /media/Windows

**I then try to mount the drive**
sudo mount /dev/hdb1 /media/Windows

**But I get the following error in the terminal**
you must specify the filesystem type

---

### Post by ILikeLinux on 2006-02-18
Just put the type of filesystem also, will be ok. Since 
this is vfat, as you said, it should be

sudo mount -t vfat /dev/hdb1 /media/windows

---

### Post by ade234uk on 2006-02-18
I got the following error

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I type the following **sudo fdisk -l** it shows the following information

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 13.6 GB, 13676544000 bytes
255 heads, 63 sectors/track, 1662 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        1662    13341982+   f  W95 Ext'd (LBA)
/dev/hdb5               2        1662    13341951    b  W95 FAT32

---

### Post by ade234uk on 2006-02-18
Its ok I sorted it. I was trying to mount the extended partition of the drive

sudo mount -t vfat /dev/hdb5 /media/windows

mounted the drive. I can now see this on the desktop.

Thank you for your help.

---

