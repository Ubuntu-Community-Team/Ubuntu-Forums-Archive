---
title: "USB drive format?"
date: 2009-03-25
forum: General Help
---

### Post by 311005901 on 2009-03-25
I'm about to format my USB drive in gParted to Fat32, but I was wondering...

Is it possible to format the drive into EXT3 and use it on Windows and OSX machines?

---

### Post by anjilslaire on 2009-03-25
Windows & OSX do not read EXT3, best to use fat32

---

### Post by 311005901 on 2009-03-25
Ok thanks!

---

### Post by mb_webguy on 2009-03-25
Windows can mount ext3 as ext2 if you use an external driver, and Mac OS X can mount ext3 natively as ext2, but neither of them can mount ext3 as ext3.  For maximum portability, FAT32 is the way to go.

---

### Post by Meow27 on 2009-03-25
do macs read ntfs?

im throwing it in cause the title didnt specify if it was flash or not :P

---

### Post by mb_webguy on 2009-03-25
I'm not sure if they can read ntfs natively, but they can use the OS X version of [ntfs-3g]("http://www.ntfs-3g.org/releases.html").

---

