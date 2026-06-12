---
title: "media hard disk not opening(permission denied)?"
date: 2009-05-04
forum: General Help
---

### Post by abhilashm86 on 2009-05-04
i have 3 partitions in my 80 GB hard disk,

abhilash@abhilash-desktop:~$ sudo fdisk -l

```
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

```
but i'm not able to open those disks, error is given,
```
Error org.freedesktop.DBus.Error.AccessDenied.

```
but when i'm superuser i can access those disks, please help

---

