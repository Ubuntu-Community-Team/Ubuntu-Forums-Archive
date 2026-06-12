---
title: "External drives/memory is read only"
date: 2009-01-21
forum: General Help
---

### Post by Meizulo on 2009-01-21
Any time I go to plug an external USB, hard drive or SD card, it come up as being READ ONLY, which is really fustrating. Anyone got any ideas...

PS: I have tried using the chmod command, but no dice

---

### Post by Crafty Kisses on 2009-01-21
What version of Ubuntu are you using? Can you access the drives if you do the following?
```
gksu nautilus
```
Can you browse the drives or write to them then? If you can't then try installing this package:
```
sudo aptitude update
sudo aptitude install ntfs-3g ntfs-config
```
I'd also like to see the results of this command:
```
sudo fdisk -l
```

---

### Post by Meizulo on 2009-01-21
I am using Ubuntu 8.04 LTS
I can access all my files and folders, but I cannot write to them. When I go into permissions, I get "The permission of /media/disk-1 could not be determined"
Here are the results you asked for:
[HTML]Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4099216e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe03efb3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9355    75144006   83  Linux
/dev/sdb2            9356        9729     3004155    5  Extended
/dev/sdb5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdc: 1004 MB, 1004012032 bytes
45 heads, 44 sectors/track, 990 cylinders
Units = cylinders of 1980 * 512 = 1013760 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1981     1960832+   6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 4, 4) logical=(0, 5, 36)
Partition 1 has different physical/logical endings:
     phys=(972, 44, 44) logical=(1980, 34, 24)
[/HTML]

---

