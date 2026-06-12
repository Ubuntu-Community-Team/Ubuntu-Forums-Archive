---
title: "Can't see my USB disk"
date: 2009-01-21
forum: General Help
---

### Post by sbasak on 2009-01-21
I am running Ubuntu from USB disk.

But when I'm within Ubuntu, I can't see my USB disk in file manager.

My disk is 8 GB and Ubuntu is taking only 3 GB or so. The rest of space I can use for copying files from Windows. But within Ubuntu I can't find this USB disk.

:(

PS: The USB disk is /dev/sdb
In GParted, I can see whole disk is showing as /dev/sdb1

---

### Post by taurus on 2009-01-21
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by sbasak on 2009-01-21
Disk /dev/sda: 60.0 GB, 60022480896 bytes
240 heads, 63 sectors/track, 7753 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2774    20971408+   7  HPFS/NTFS
/dev/sda2            2775        7753    37641240    f  W95 Ext'd (LBA)
/dev/sda5            2775        7753    37641208+   7  HPFS/NTFS

Disk /dev/sdb: 8088 MB, 8088715264 bytes
5 heads, 32 sectors/track, 98739 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Disk identifier: 0x000ed8ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          51       98740     7895104    c  W95 FAT32 (LBA)

---

### Post by sbasak on 2009-01-22
Apologies for bump.

Still couldn't see my USB drive where I'm running Ubuntu from.
:(

---

### Post by taurus on 2009-01-22
Try mounting it with

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```
And once you are done with it, don't just unplug it.  You need to unmount it first before you unplug it.  You can unmount it by clicking the little icon on the desktop with the right button or from a terminal.

```
sudo umount /media/sdb1
```

---

### Post by dcovnton on 2012-12-03
I am having issues with Ubuntu 12.10 detecting my 16GB USB jump drive.
When I do an sudo fdisk -l  I get

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006aeb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  2930276351  1464887297    5  Extended
/dev/sda5          501760  2930276351  1464887296   83  Linux

Disk /dev/mapper/sda5_crypt: 1500.0 GB, 1500042493952 bytes
255 heads, 63 sectors/track, 182369 cylinders, total 2929770496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-root: 1495.7 GB, 1495718166528 bytes
255 heads, 63 sectors/track, 181844 cylinders, total 2921324544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 4282 MB, 4282384384 bytes
255 heads, 63 sectors/track, 520 cylinders, total 8364032 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

Disk /dev/sdb: 16.3 GB, 16286481920 bytes
255 heads, 63 sectors/track, 1980 cylinders, total 31809535 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    31807487    15902720    7  HPFS/NTFS/exFAT
:
Can someone help me on this one, thanks

---

