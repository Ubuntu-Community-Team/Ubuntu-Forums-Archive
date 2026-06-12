---
title: "Wine Install?"
date: 2006-03-26
forum: Gaming &amp; Leisure
---

### Post by jhartford on 2006-03-26
I feel like my Wine install is not how I should have it set up...

it is /home/wine-0.9.6/ 

instead of /home/wine/

also there is no "C:" or "windows" folder within the wine folder.  I am trying to install WoW, so far I have "winecfg" and installed the Mozilla.

---

### Post by jhartford on 2006-03-26
Hmm well I figured out the...

Go --> Location...  function so now I have found ~/.wine !  :)

---

### Post by jhartford on 2006-03-26
When I do either:

```
patch -p1 </path/to/wine-cvs-glx.diff
patch -p1 </path/to/wine-wow-fixes.patch
```

It asks me which files I want to patch........... :-k

---

### Post by jhartford on 2006-03-26
How can I copy files from my Windows partition?

---

### Post by digby on 2006-03-26
To copy files from your windows partition, you first have to make sure it's mounted.  If you didn't change it at install time (or since) it's probably /media/hda1 (if an IDE drive) or /media/sda1 (if a SATA drive).   If neither of those exist, then your drive probably isn't mounted.

To mount, do this (both commands as root or with sudo)```
#mkdir /media/windows
#mount /dev/hda1 /media/windows -t ntfs
``` If your windows drive is formated w/ FAT32, use vfat instead of ntfs.

Then you can go into /media/windows/some_folder_on_the_windows_drive/ and copy as you wish.  You may have to be root to access that folder and copy stuff from it.

Let me know if any of that isn't clear.

---

