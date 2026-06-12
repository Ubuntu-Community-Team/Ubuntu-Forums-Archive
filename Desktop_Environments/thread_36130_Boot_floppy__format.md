---
title: "Boot floppy  format"
date: 2005-05-22
forum: Desktop Environments
---

### Post by mherring on 2005-05-22
What filesystem does Ubuntu use to make the boot floppy during install?  I have tried several different options to mount the floppy, but I cant find one that works.

(I want to read and maybe edit what is on the floppy)

---

### Post by jasmuz on 2005-05-22
[QUOTE=mherring]What filesystem does Ubuntu use to make the boot floppy during install?  I have tried several different options to mount the floppy, but I cant find one that works.

(I want to read and maybe edit what is on the floppy)[/QUOTE]
 Most boot floppies use ext2, but others are written in RAW format....allowing for the allocation of 1.72 megabytes of space into a 1.44 megabyte boot floppy.

---

### Post by mherring on 2005-05-22
[QUOTE=jasmuz]Most boot floppies use ext2, but others are written in RAW format....allowing for the allocation of 1.72 megabytes of space into a 1.44 megabyte boot floppy.[/QUOTE]

I found a utility called "disktype".  It says my floppy is FAT12.

FAT12 is not an option with mount--nor is "RAW".  I have tried things like vfat and the command is successful, but there is still nothing when I "ls"

---

