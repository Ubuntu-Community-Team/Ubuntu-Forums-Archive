---
title: "RAID 0 orphan re-integration"
date: 2009-04-20
forum: General Help
---

### Post by BOlte on 2009-04-20
Hey All,

I'm a recent convert to Linux systems, and have had very little troubles (or ones that can't be sorted quickly). However, I have a RAID trouble that I can't seem to find any useful information on.

Both XP and Ubuntu are dual-boot on a sata drive, with 4 x WD-200Gb drives SIL 3114 (software) RAID-0 on the SIL card as a data-repository. This data is fed through algorithms and the result saved to back-up drives before the RAID is cleaned, ready for the next run.

After installing Ubuntu I had to work with GRUB to get my XP install operational again. In the install/GRUB process 3 of my 4 HD's were orphaned from the RAID. I guessed that the dive-header information had been lost/written over. Tools such as dmraid failed to locate a raid drive, etc. 

Below is a print of my disk partition information. 4 x 200 Gb raid drives, and a single 0.5Tb. Note the 2 boot locations?? No OS has ever existed on the raid. 

Qn: Is the assumption that the header information from the disks is missing true? ...and if so, can the raid be re-built?

Cheers!


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a9f68d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      145579      327161  1458557341   25  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2               1           3       23731   3a  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3          106526      245487  1116201026+   0  Empty
Partition 3 does not end on cylinder boundary.
/dev/sda4               1           3       23731   3a  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc98963c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       72963   586075266   42  SFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6607fee8

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       34587   277820046    7  HPFS/NTFS
/dev/sde2           34588       34891     2441880   82  Linux swap / Solaris
/dev/sde3           34892       37337    19647495   83  Linux
/dev/sde4           37338       60801   188474580    f  W95 Ext'd (LBA)
/dev/sde5           37338       42200    39062016   83  Linux
/dev/sde6           42201       60801   149412501   83  Linux

---

### Post by fjgaude on 2009-04-20
I can't say what has happened... what does the BIOS startup say when go into the SIL setup menu?

---

### Post by BOlte on 2009-04-20
In the SIL menue it says:

(abreviated...)

Physical     logical
-------------------------
HD-1-200G  | HD-1-200G
HD-2-200G  |
HD-3-200G  | Reserved
HD-4-200G  |

I've been able to use my sector-hack tools in Windows (still more familiar there) to dump HD images to disk. Sifted through a few raid-emulation software tools and managed to save the data (100%). 

Would still like to know what went wrong though, and if it's going to happen again if I erase the raid and install a new one that works...

---

### Post by fjgaude on 2009-04-21
Good for you! I don't think I can help here. I know that a few use dmraid with success, AFAIK. I've left Windows so long ago I can't recall what's good about it. <smile>

I'm a graphic designer and use mdadm software raid for my raid5 array. Has worked fine for years and years.

---

