---
title: "Weird FAT32 problem"
date: 2009-03-01
forum: General Help
---

### Post by gfxfreak on 2009-03-01
I have a 30 GB FAT32 partition, formatted with gparted, when one day I booted to Windows Vista Ultimate x86 I tried to access the partition and it turned out that format is needed, the partition is seen as RAW, but in Ubuntu I can use it normally, even fsck'ed it and no problems.

Any ideas?

Thanks in advance.

---

### Post by jyaan on 2009-03-01
Sounds like the partition isn't actually FAT32. I'd re-check in Ubuntu by looking at its properties. But you used it in Windows before?

---

### Post by gfxfreak on 2009-03-01
Honestly I don't remember to have used it, but I'm quite sure it is FAT32, look here is my fdisk -l output:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes**-> 1st hard drive, doesn't apply**
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5da5d19d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3833    30788541    7  HPFS/NTFS
/dev/sda2            3834        5130    10418152+   b  W95 FAT32
/dev/sda3            5131        9729    36941467+   5  Extended
/dev/sda5            5131        9444    34652173+  83  Linux
/dev/sda6            9445        9729     2289231   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00034c34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+  1c  Hidden W95 FAT32 (LBA) **-> hidden partition**
/dev/sdb2            2551       30401   223713157+   5  Extended
/dev/sdb5            2551        8956    51456163+   b  W95 FAT32 **-> THIS IS IT!**
/dev/sdb6            8957       21737   102663351    7  HPFS/NTFS
/dev/sdb7           21738       30089    67087408+  83  Linux
/dev/sdb8           30090       30401     2506108+  82  Linux swap / Solaris


```

Ok, the hidden partition isn't formatted, cause the hard drive have some bad sectors, fixed it with specialized software, repartitioned with gparted.
The partition I'm talking about is labeled so there is no way I'm confused.

---

