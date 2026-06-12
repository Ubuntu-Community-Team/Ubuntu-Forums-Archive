---
title: "Need a partitioning solution"
date: 2009-04-20
forum: General Help
---

### Post by RuleMaker on 2009-04-20
My partitions are all messed up...I'd be happy if I could format the whole HD but right now I'm not in a situation to do that.

This is how it looks like:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            9472        9602     1052257+  82  Linux swap / Solaris
/dev/sda2   *           1        9471    76075776    f  W95 Ext'd (LBA)
/dev/sda3            9603        9964     2907765   83  Linux
/dev/sda5               1        6375    51207124+  83  Linux
/dev/sda6            6376        9192    22627521    7  HPFS/NTFS
/dev/sda7            9193        9471     2241036   83  Linux

Looks pretty bad, huh...especially if you want to merge **sda3** and **sda7** and besides that you can only delete the swap partition which is **sda1**.
Each partition is separated by another which i have to keep.
**sda6** is my storage partition, I keep all my music there...can't delete it and also I don't have enough free space on other partitions to move it there (even if I'd like to get rid of that NTFS partition which is there from old days).
**sda5** is my mint linux partition, I still want to keep it.
And finally **sda2** which is the extended partition.

Any solutions how to merge sda3 and sda7?

---

### Post by coffeecat on 2009-04-20
> **RuleMaker said:**
> Any solutions how to merge sda3 and sda7?

You can't. sda3 is a primary partition. sda7 is a logical contained in your extended partition (sda2). However, there may be a way around, but we need more information. Post exactly what is on each partition. You haven't said what is on sda3 and sda7.

Also, please post the size of each partition in GB. You've omitted the first part of the output of fdisk -l, so we don't even know how big the whole disc is.

---

### Post by RuleMaker on 2009-04-20
80 Gb HD.
sda3 and sda7 are empty and free to delete, move and modify in any way.
Now I'm trying to move all the music from my sda6 to other partitions, mp3 and my USB flash memory. I want to finally delete that NTFS partition.
Here is a whole output of fdisk -l:
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef1aef1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            9472        9602     1052257+  82  Linux swap / Solaris
/dev/sda2   *           1        9471    76075776    f  W95 Ext'd (LBA)
/dev/sda3            9603        9964     2907765   83  Linux
/dev/sda5               1        6375    51207124+  83  Linux
/dev/sda6            6376        9192    22627521    7  HPFS/NTFS
/dev/sda7            9193        9471     2241036   83  Linux

Partition table entries are not in disk order

---

