---
title: "How to make my usb drive executable?"
date: 2007-07-07
forum: Desktop Environments
---

### Post by yinglcs2 on 2007-07-07
hi,

I hook up my ubuntu to an external hard drive, but when i try to compile code, I get this error:

/media/LINUXBACKUP/backup/mozilla2.0.0.1-/mozilla/firefox-objdir/config/nsinstall: cannot make symbolic link /media/LINUXBACKUP/backup/mozilla2.0.0.1-/mozilla/firefox-objdir/dist/include/nsBuildID.h: Operation not permitted

Can you please tell me how can I fix it? How can I make symbolic link on a external usb drive?

Thank you.

---

### Post by Martje_001 on 2007-07-07
Symbolic links don't work with FAT32 (AFAIK).

---

### Post by fjgaude on 2007-07-07
> **yinglcs2 said:**
> hi,

I hook up my ubuntu to an external hard drive, but when i try to compile code, I get this error:

/media/LINUXBACKUP/backup/mozilla2.0.0.1-/mozilla/firefox-objdir/config/nsinstall: cannot make symbolic link /media/LINUXBACKUP/backup/mozilla2.0.0.1-/mozilla/firefox-objdir/dist/include/nsBuildID.h: Operation not permitted

Can you please tell me how can I fix it? How can I make symbolic link on a external usb drive?

Thank you.

Are you compiling code for Linux? Is the external drive file type ext3? or ext2? or what?

frank

---

### Post by yinglcs2 on 2007-07-08
It shows 'File System: vfat (FAT32).

---

