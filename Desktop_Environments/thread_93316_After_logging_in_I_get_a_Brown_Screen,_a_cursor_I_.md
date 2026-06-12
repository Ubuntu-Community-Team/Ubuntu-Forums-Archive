---
title: "After logging in I get a Brown Screen, a cursor I can move, and no Gnome"
date: 2005-11-21
forum: Desktop Environments
---

### Post by kilovh on 2005-11-21
This is not fixed by changing my video drivers to either vesa, or nvidia, or back to nv. I have tried all of these. I didn't have this problem before the reboot.

Also, another problem I didn't have before the reboot is accessinbg my 2nd harddrive, which is an NTFS. I can only access it now as Root, and even as root it will not allow me to change the permissions on the hard drive, saying that its read-only.

Please help.

Thanks, kilovh.

---

### Post by aysiu on 2005-11-26
[QUOTE=kilovh]This is not fixed by changing my video drivers to either vesa, or nvidia, or back to nv. I have tried all of these. I didn't have this problem before the reboot.[/quote] Try [this search](http://www.ubuntuforums.org/search.php?searchid=2671105).

> 
Also, another problem I didn't have before the reboot is accessinbg my 2nd harddrive, which is an NTFS. I can only access it now as Root, and even as root it will not allow me to change the permissions on the hard drive, saying that its read-only.

Please help.

Thanks, kilovh. NTFS is read-only. That's how it is in Linux. If you want read/write, try FAT32 instead. If you want the user (instead of root) to have read-only access to NTFS, try following these instructions: [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

