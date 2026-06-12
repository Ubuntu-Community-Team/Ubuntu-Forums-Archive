---
title: "unknown filesystem type 'xfs'"
date: 2009-04-20
forum: General Help
---

### Post by aurora79 on 2009-04-20
Hi, I have running BackTrack 4 system and as your knows it is working on ubuntu.

While I try to mount a partition it says

unknown filesystem type 'xfs'

How can I resolve it?

here is fdisk -l output:

root@bt:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfccdfccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9728    37182442+   f  W95 Ext'd (LBA)
/dev/sda5            5100        9728    37182411    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69048008

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         125     1004031    5  Extended
/dev/sdb2             126       60801   487379970   83  Linux
/dev/sdb5               1          16      128457   82  Linux swap / Solaris
/dev/sdb6              17          17        8001   83  Linux
/dev/sdb7              18          18        8001   83  Linux
/dev/sdb8              19          34      128488+  83  Linux
/dev/sdb9              35         125      730926   83  Linux

sdb2 is xfs format which is I wanted the mount.

---

### Post by Yashiro on 2009-04-20
Try installing xfsprogs, xfsdump and gparted from the repositories.

Which Ubuntu are you using?

---

