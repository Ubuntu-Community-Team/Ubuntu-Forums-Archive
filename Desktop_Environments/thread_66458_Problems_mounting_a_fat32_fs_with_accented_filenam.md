---
title: "Problems mounting a fat32 fs with accented filenames"
date: 2005-09-17
forum: Desktop Environments
---

### Post by dierre on 2005-09-17
Hi,

I would like to mount a fat32 filesystem that contains some files whose names have accented (Italian) letters.

I have tried playing around with mount options, namely uni_xlate, utf8, codepage but I cannot get it to work, as the accented characters do not display correctly in nautilus or the terminal...

Could anybody please help me? THANK YOU!

---

### Post by taxus on 2005-09-17
I mount 2 FAT32 partitions and their French accented characters show correctly in both Windows XP and Linux. This is one of my /etc/fstab entries (taken from the Ubuntu-fr.org wiki):
```
/dev/hda5 /doc vfat user,auto,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850 0 0
```
Codepage 850 is the multilingual/international code page in DOS. I don't see why it shouldn't work for Italian, as DOS manuals list it as default (with 437 which is really for US English) code page for Italian. Have you tried that value?

Defaults are "iocharset=iso8859-1" and "codepage=437". With gid and uid I'm setting write permission to my account and to my group.

[Edit]Darn, I don't know why "utf8" gets separated, it shouldn't. It's "iocharset=utf8".

---

