---
title: "FAT32 partition recovery"
date: 2008-12-04
forum: General Help
---

### Post by Lechio on 2008-12-04
My secondary HD is formated using the FAT32 file system.
After halting my computer and booting again this partition decided to stop mounting. I get this after trying to mount it:

FAT: bogus logical sector size 544
VFS: Can't find a valid FAT filesystem on dev sdb1.

When trying to check it with "fsck.vfat" I get:
File system has -769 clusters but only space for 2228222 FAT entries.

The output of "fdisk -l" correctly detects the partition as being "W95 FAT32 (LBA)", and its size is also correct.

What happen? Is it lost for good, or can the partition be recovered?
Help. :(

---

### Post by Lechio on 2008-12-04
Bump.
No-one...? :/

---

### Post by Lechio on 2008-12-05
Managed to salvage it using testdisk. Had to rebuild the FAT boot sector and its table.
Found this page useful if anyone runs into this same problem: [http://www.cgsecurity.org/wiki/Advanced_FAT_Repair](http://www.cgsecurity.org/wiki/Advanced_FAT_Repair)

---

