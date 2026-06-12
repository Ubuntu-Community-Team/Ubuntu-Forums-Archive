---
title: "ext3 drive"
date: 2005-04-26
forum: Desktop Environments
---

### Post by anakite on 2005-04-26
Just made a ext3 seperation on my hd that i can't figure out how to see. What am i doing wrong? 
Note: Begginer.

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=anakite]Just made a ext3 seperation on my hd that i can't figure out how to see. What am i doing wrong? 
Note: Begginer.[/QUOTE]

You need to mount it. Type this in the terminal:

sudo fdisk -l

copy and paste back what it says.

---

### Post by anakite on 2005-04-27
[QUOTE=poofyhairguy]You need to mount it. Type this in the terminal:

sudo fdisk -l

copy and paste back what it says.[/QUOTE]

here it is..
> Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2490    20000893+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         788     6329578+  83  Linux
/dev/hdb2             789        9729    71818582+   5  Extended
/dev/hdb5             828         958     1052257+  83  Linux
/dev/hdb6            3156        9729    52805623+   7  HPFS/NTFS
/dev/hdb7             789         827      313204+  82  Linux swap / Solaris
/dev/hdb8             959        3155    17647371   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

---

