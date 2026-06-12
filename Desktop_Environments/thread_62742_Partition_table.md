---
title: "Partition table"
date: 2005-09-05
forum: Desktop Environments
---

### Post by Capilano on 2005-09-05
Hello all;

Can someone explain how to fix this situation, please.
I repartitioned hdb1, using Qparted. The goal was to setup a partition FAT32 to eventually install WinXP.

In a terminal, when I do : sudo fdisk-l the returned answer is as follow:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1897    15237621   83  Linux
/dev/hda2            4811        4998     1510110    5  Extended
/dev/hda3            1898        4810    23398672+  83  Linux
/dev/hda5            4811        4998     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       47638    24009111    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdb2           47638       95275    24009142+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hdb3           95275      238202    72035460   83  Linux
Partition 3 does not end on cylinder boundary.

Disk /dev/hdd: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        1277    10257471   83  Linux
/dev/hdd3            1278        7476    49793467+  83  Linux


Thank you all.

---

