---
title: "grub-install error ???"
date: 2005-12-08
forum: General Help
---

### Post by bslusser on 2005-12-08
ubuntu@ubuntu:~$ sudo grub-install /dev/hde
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/casper-snapshot does not have any corresponding BIOS drive.

I am booting from a livecd and trying to install grub onto the mbr.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hde: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        5602    44992552+   c  W95 FAT32 (LBA)
/dev/hde2            5603       11973    51175057+  83  Linux
/dev/hde3           11974       12161     1510110    5  Extended
/dev/hde5           11974       12161     1510078+  82  Linux swap / Solaris

Disk /dev/hdg: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1        4677    37567971   83  Linux
/dev/hdg2            4678        4865     1510110    5  Extended
/dev/hdg5            4678        4865     1510078+  82  Linux swap / Solaris


I am not having any luck with dual booting windows and ubuntu. grub never seems to install right onto the mbr. any suggestions would be appreciated.

---

