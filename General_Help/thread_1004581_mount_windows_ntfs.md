---
title: "mount windows ntfs"
date: 2008-12-07
forum: General Help
---

### Post by divinequran on 2008-12-07
how to mount the windos on my linux machine, i have songs in my windows drive i try to copy it mounting it. when i try to mount it states error message unkown filesystem 'NTFS'

---

### Post by taurus on 2008-12-07
Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

p.s.  That is a lower case letter L.

---

### Post by divinequran on 2008-12-09
Hi,
 i get the answer as follows,

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/sda5            1276        3825    20482843+   7  HPFS/NTFS
/dev/sda6            3826        6630    22531131    7  HPFS/NTFS
/dev/sda7            6631        6764     1076323+  83  Linux
/dev/sda8            6765        9728    23808298+  8e  Linux LVM

---

