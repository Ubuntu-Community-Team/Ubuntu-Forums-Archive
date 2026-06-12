---
title: "Usb harddrive mounts multiple time"
date: 2009-03-11
forum: General Help
---

### Post by asimon623 on 2009-03-11
alex@alex-laptop /media $ ls
BlackExternal     BlackExternal____     BlackExternal________    cdrom0
BlackExternal_    BlackExternal_____    BlackExternal_________
BlackExternal__   BlackExternal______   BlackExternal__________
BlackExternal___  BlackExternal_______  cdrom


i have no idea why this would happen.
any clues?

---

### Post by asimon623 on 2009-03-12
bueller?

---

### Post by asimon623 on 2009-03-17
Here is the fdisk which I think is showing an even weirder situation:

```
alex@alex-laptop ~ $ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb318eac5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris
Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb6b7d8fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sdc5               2      121601   976751968+   7  HPFS/NTFS
/dev/sdc6               2      121601   976751968+   7  HPFS/NTFS
/dev/sdc7               2      121601   976751968+   7  HPFS/NTFS
/dev/sdc8               2      121601   976751968+   7  HPFS/NTFS
/dev/sdc9               2      121601   976751968+   7  HPFS/NTFS
/dev/sdc10              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc11              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc12              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc13              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc14              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc15              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc16              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc17              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc18              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc19              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc20              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc21              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc22              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc23              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc24              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc25              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc26              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc27              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc28              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc29              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc30              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc31              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc32              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc33              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc34              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc35              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc36              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc37              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc38              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc39              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc40              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc41              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc42              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc43              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc44              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc45              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc46              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc47              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc48              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc49              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc50              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc51              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc52              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc53              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc54              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc55              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc56              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc57              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc58              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc59              2      121601   976751968+   7  HPFS/NTFS
/dev/sdc60              2      121601   976751968+   7  HPFS/NTFS

```

---

