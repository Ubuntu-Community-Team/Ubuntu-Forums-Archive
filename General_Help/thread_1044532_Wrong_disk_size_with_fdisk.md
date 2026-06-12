---
title: "Wrong disk size with fdisk"
date: 2009-01-19
forum: General Help
---

### Post by koetjeboeh on 2009-01-19
Hi all,

A question regarding disk size. I am trying to clone my hd:

[http://www.linux.com/feature/152592](http://www.linux.com/feature/152592)

My 40 GB has to be cloned to a new 250 GB one. My pc is a Dell, the new HD is from Dell, so should work. Unfortunately I'm running into some problems. When I boot with an Ubuntu live CD and check both HD's: 

$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09740974

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1946    15631213+   7  HPFS/NTFS
/dev/sda2            1947        2675     5855692+  83  Linux
/dev/sda3            2676        2799      996030   82  Linux swap / Solaris
/dev/sda4            2800        4863    16579080   83  Linux

Disk /dev/sdb: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f207f20

Disk /dev/sdb doesn't contain a valid partition table

The size is wrong. The disk is 250 GB, no 2 TB.

What can cause this? Live cd version is 8.04. The original HD is connected on the motherboard, the second ons via an SATA / USB converter. Can this be the cause of this problem?

Regards,
Fabio

---

