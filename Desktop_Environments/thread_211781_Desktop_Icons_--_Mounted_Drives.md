---
title: "Desktop Icons -- Mounted Drives"
date: 2006-07-08
forum: Desktop Environments
---

### Post by endfx on 2006-07-08
I have a harddrive that has a fat32 filesystem.
Whenever I mount it, the gnome desktop creates an icon for it on my desktop.

Problem is, the name of this icon is really weird characters/symbols.
The mounted partition works just fine, its just that the icon gets a weird name:

"L,M_" and then 3 box symbols.

Can I change what the desktop names this icon?

Note: The partition that is mounted is /dev/hdb2 and is mounted to /media/hdb2.
All my other partitions (NTFS) that are mounted display just find as icons on the desktop.

Can anyone solve this annoyance?

Thanks.

---

### Post by Dubbayoo on 2006-07-08
I believe the name it uses is the disklabel so you have to change that.

---

### Post by tturrisi on 2006-07-08
if you boot to windows and rename it then next boot to ubuntu will reflect the new name.

---

### Post by endfx on 2006-07-09
Thanks! That worked.

---

