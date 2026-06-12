---
title: "Access USB disk via LAN"
date: 2009-06-16
forum: Desktop Environments
---

### Post by sness on 2009-06-16
I have a USB disk (my book) connected to a laptop that should be available to Windows users. I have installed Samba, and can access the disk from other machines, but not the USB disk. The USB disk is shown in the network, but when I try to access the disk I get the message: The disk is not awailible.
I can’t change the permissions on the Disk in Nautilus.

--------------------------------------------
root@sn-laptop:/etc# fdisk -l

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd890d890

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1475     2080417+  83  Linux
/dev/sda3            1476        2432     7687102+   5  Extended
/dev/sda5            2312        2432      971901   82  Linux swap / Solaris
/dev/sda6            1476        2268     6369709+  83  Linux
/dev/sda7            2269        2311      345366   82  Linux swap / Solaris

Partition table entries are not in disk order

[COLOR="Red"]Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)[/COLOR]

-------------------------------------------------------------------------------

root@sn-laptop:/media# ls -la
total 58
drwxr-xr-x  7 root root  4096 2009-06-15 10:26 .
drwxr-xr-x 21 root root  4096 2009-06-12 21:23 ..
lrwxrwxrwx  1 root root     6 2008-06-23 18:44 cdrom -> cdrom0
dr-xr-xr-x 10 root root  2048 2008-10-30 00:24 cdrom0
drwxr-xr-x 21 root root  4096 2007-10-19 08:02 disk
lrwxrwxrwx  1 root root     7 2008-06-23 18:44 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2008-06-23 18:44 floppy0
-rw-r--r--  1 root root   232 2009-06-15 10:26 .hal-mtab
-rw-------  1 root root     0 2009-06-13 22:18 .hal-mtab-lock
drwxr-xr-x 11 root root  4096 2008-06-23 18:40 -home
[COLOR="Red"]drwx------ 17 sn   root 32768 1970-01-01 01:00 My Book[/COLOR]
root@sn-laptop:/media#[COLOR="Red"][/COLOR]

---

