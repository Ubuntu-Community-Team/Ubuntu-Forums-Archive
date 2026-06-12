---
title: "mount the removable devices......"
date: 2009-05-09
forum: General Help
---

### Post by abhilashm86 on 2009-05-09
i need to always mount my hard disk in ubuntu i know in /etc/fstab to make auto boot, but not exactly know, please help how to do,

```
abhilash@abhilash-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff4bff4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433        9729    58613152+   f  W95 Ext'd (LBA)
/dev/sda5            2433        2476      353398+   e  W95 FAT16 (LBA)
/dev/sda6            2477        4760    18346198+  83  Linux
/dev/sda7            4761        4865      843381   82  Linux swap / Solaris
/dev/sda8            4866        7299    19542568+   b  W95 FAT32
/dev/sda9            7299        9729    19519888+   b  W95 FAT32
abhilash@abhilash-desktop:~$ sudo blkid
/dev/sda1: UUID="5AB85F79B85F529D" TYPE="ntfs" 
/dev/sda6: UUID="c098dd08-8b82-4dd6-b2b1-fff959ab7870" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="53b39459-d52d-4d6a-bdb2-1e6bfcabfb36" 
/dev/sda8: LABEL="SONGS" UUID="71B1-0D79" TYPE="vfat" 
/dev/sda9: LABEL="MUSIC" UUID="DCC5-0AE8" TYPE="vfat" 

```
also i want to learn how exatly its done, just explain..........

---

