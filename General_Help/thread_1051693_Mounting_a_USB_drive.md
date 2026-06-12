---
title: "Mounting a USB drive"
date: 2009-01-27
forum: General Help
---

### Post by Revenged on 2009-01-27
I have NO idea how to do this, and I need to take a paper to school to print.

The USB drive is plugged in, but doesn't show up in the partition editor. 

Any help?

---

### Post by Boomhauer on 2009-01-27
you go to a terminal and enter in ```
sudo fdisk -l
``` paste back here what it returns

---

### Post by Revenged on 2009-01-27
```
Disk /dev/sda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2388    19181578+  83  Linux
/dev/sda2            2389        2498      883575    5  Extended
/dev/sda5            2389        2498      883543+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
63 heads, 46 sectors/track, 337050 cylinders
Units = cylinders of 2898 * 512 = 1483776 bytes
Disk identifier: 0x5e3fa9fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      337051   488384512    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa28fa28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6439    51721236    7  HPFS/NTFS
/dev/sdc2            6440       30401   192474765    7  HPFS/NTFS

```

---

### Post by Boomhauer on 2009-01-27
are you trying to mount the 500gb drive or the 250gb drive
edit:  if it isnt either one of these drives, are you sure the drive is plugged in?  does it look/sound like it is on?

---

### Post by Revenged on 2009-01-27
> **Boomhauer said:**
> are you trying to mount the 500gb drive or the 250gb drive

Neither.

I'm trying to mount an 8 gig USB flash drive.

---

### Post by Revenged on 2009-01-27
Anyone?

---

