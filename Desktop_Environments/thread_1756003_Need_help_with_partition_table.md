---
title: "Need help with partition table"
date: 2011-05-11
forum: Desktop Environments
---

### Post by Cyclops_ on 2011-05-11
I was an idiot, and tried to manage my partition table with Windows.  My drive (sda) had on it a Windows installation and an Ubuntu installation.  I was trying to delete a particular partition, but accidentally deleted more than that!

So... in an attempt to recover lost data (I don't want to lose my data!) I used the testdisk utility.  I did the Analyze bit, and it found all of my partitions!  I clicked on [Write], and it wrote it.

However - gparted still doesn't see the partitions.  There is a mismatch on the cylinders, I'm thinking.  

When I do an sfdisk -d /dev/sda > somefile.txt it also tells me "Warning: extended partition does not start at a cylinder boundary."

Here is output of fdisk -l :

```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5a522f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1254    10066944    7  HPFS/NTFS
/dev/sda2            1254        1267      102400    7  HPFS/NTFS
/dev/sda3            1267        5275    32194332+   7  HPFS/NTFS
/dev/sda4            5275       77826   582772617    f  W95 Ext'd (LBA)
/dev/sda5            5275       11904    53251072   83  Linux
/dev/sda6           11904       18347    51755008   83  Linux
/dev/sda7           18348       20779    19529728   83  Linux
/dev/sda8           20779       67561   375776380   83  Linux
/dev/sda9           76340       77826    11936760   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

```

Any and all help would be incredibly appreciated

---

