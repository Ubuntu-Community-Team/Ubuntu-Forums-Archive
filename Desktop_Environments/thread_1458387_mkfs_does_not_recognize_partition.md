---
title: "mkfs does not recognize partition"
date: 2010-04-19
forum: Desktop Environments
---

### Post by bluethundr on 2010-04-19
I just unmounted a volume known as /dev/sd2a and created a partition on it with fdisk. but when I try to format it with mkfs.ext3 it reports that the partition I created isn't there even tho fdisk reports that it is. I made sure to reboot after using fdisk

```

root@cloud2:~# fdisk /dev/sda2

The number of cylinders for this disk is set to 19464.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda2: 160.1 GB, 160104972288 bytes
255 heads, 63 sectors/track, 19464 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sda2p1               1        1246    10008463+  83  Linux

Command (m for help): 



root@cloud2:~# mkfs.ext3 -O dir_index /dev/sda2p1
mke2fs 1.38 (30-Jun-2005)
Could not stat /dev/sda2p1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

```

Why won't mkfs recognize the partition I created with fdisk?

---

