---
title: "Cloned Disk - sector size"
date: 2014-06-15
forum: Desktop Environments
---

### Post by Geoff_Lane on 2014-06-15
Folks,

After a few hiccups I have managed to dd copy my old 250GB HD onto a new 500GB drive (haven't tested it yet though).

I am aware I cannot use both disks together due to ID problems and I will have to resize the cloned disk as it will show as 250GB

What I would like to ask if anyone can throw any light on potential problems with different sector sizes.

When I ran sudo fdisk -l all was identical except the I/O size (minimum/optimal): my original disk is 512 and the cloned one is 4096

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d36f6b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   416641023   208319488    7  HPFS/NTFS/exFAT
/dev/sda2       467085312   488390655    10652672    7  HPFS/NTFS/exFAT
/dev/sda3       416641024   424509439     3934208   82  Linux swap / Solaris
/dev/sda4       424509440   467085311    21287936   83  Linux

Partition table entries are not in disk order


Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4d36f6b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   416641023   208319488    7  HPFS/NTFS/exFAT
/dev/sdd2       467085312   488390655    10652672    7  HPFS/NTFS/exFAT
/dev/sdd3       416641024   424509439     3934208   82  Linux swap / Solaris
/dev/sdd4       424509440   467085311    21287936   83  Linux

Partition table entries are not in disk order

In the dd command I did use bs 4096

Could this cause a problem of should I recopy using bs 512 before I install the new HD into laptop.

Geffers

---

