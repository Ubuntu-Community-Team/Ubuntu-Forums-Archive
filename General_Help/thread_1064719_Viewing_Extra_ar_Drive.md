---
title: "Viewing Extra ar Drive"
date: 2009-02-09
forum: General Help
---

### Post by dazzler on 2009-02-09
Can anyone help me i have 3 Hard Drives, 1 Vista, 1 Ubuntu and one Sata where i keep multimedia files i can see the Vista Drive (Although i dont really want to) but not my data drive heres some more info from fdisk: -

Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xc620c620

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      484519   244197544+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5b657bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18701   150215751   83  Linux
/dev/sdb2           18702       19457     6072570    5  Extended
/dev/sdb5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
49 heads, 1 sectors/track, 11961524 cylinders
Units = cylinders of 49 * 512 = 25088 bytes
Disk identifier: 0x0d1e77c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2    11961525   293057320+   7  HPFS/NTFS

Thanks

---

### Post by logos34 on 2009-02-10
try to mount sda1 manually:

[https://help.ubuntu.com/community/MountingWindowsPartitions#For%20FAT32%20and%20FAT16%20Partitions](https://help.ubuntu.com/community/MountingWindowsPartitions#For%20FAT32%20and%20FAT16%20Partitions)

add a line for sda1 to /etc/fstab so it automounts at boot:

[https://help.ubuntu.com/community/Fstab#File%20System%20Specific%20Examples](https://help.ubuntu.com/community/Fstab#File%20System%20Specific%20Examples)

hope that helps

---

