---
title: "Dual boot WinXP/Ubuntu"
date: 2009-01-20
forum: General Help
---

### Post by fluffyflester on 2009-01-20
Hey ubunters, help pl0x
I installed ubuntu 8.04 and now I'm trying to install WinXP x64 Pro through USB Flash drive ( No CD drive ). ( I installed it on my USB flash drive with USBmultiboot )
When I select the extended partition I made for windows, it says that it can't install the MBR because the file system is unkown on the main partition.
Here's my fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004cf77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26         917     7164990   83  Linux
/dev/sda3             918       15217   114864750   83  Linux
/dev/sda4           15218       19457    34057800    5  Extended
/dev/sda5           15218       15478     2096451   82  Linux swap / Solaris
/dev/sda6           15479       19456    31953253+   e  W95 FAT16 (LBA)

I wanted to install windows on sda6.
How should I proceed?

---

