---
title: "Unbuntu Desktop's NTFS Filesystem Reference"
date: 2006-06-30
forum: Desktop Environments
---

### Post by agajardo on 2006-06-30
I'm curious as to finding out how to go about removing the reference to my windows (ntfs) filesystem 'device' found in the "Computer - File Browser" window since it is not accessible through Ubuntu and there is no sense in cluttering the file browser with unaccessible icons.  This 'device' is really just the first partition (sda1) of my hard drive, where my windows xp operating system resides.  Ubuntu root is sda2 and swap is sda3.  The ntfs filesystem device (sda1) is not mounted (not listed in fstab file, nor in mtab) yet the reference to the windows partition remains in the 'Computer - File Browser' window.

If anyone could instruct me as to how to go about removing this useless reference from the file browser, your help would be much appreciated.

Thanks.

---

### Post by falcon15500 on 2006-06-30
[QUOTE=agajardo]I'm curious as to finding out how to go about removing the reference to my windows (ntfs) filesystem 'device' found in the "Computer - File Browser" window since it is not accessible through Ubuntu and there is no sense in cluttering the file browser with unaccessible icons. [/QUOTE]

  NTFS partitions can be read from Ubuntu by default, and with a little work can even be written to (still experimental).  I read from my NTFS partition all the time and my setup sounds very similar to yours (win on sda1, linux on sda2).

falc

---

