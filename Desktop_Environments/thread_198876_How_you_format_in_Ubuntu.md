---
title: "How you format in Ubuntu?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by LoganT on 2006-06-17
I want to format my hard drive. Is there a command line I can type in?

---

### Post by user1397 on 2006-06-17
you can use gparted, a graphical partitioner for gnome.  you can use the ubuntu-desktop-cd which already contains gparted, but you can't use gparted with your installed ubuntu, except for unmounted partitions. (you can't edit mounted partitons.)

---

### Post by Alpha_Cluster on 2006-06-17
Well you got two options.  If you want a gui i believe you can get Gparted.  But if you got some idea of what your doin you can just use fdisk.

---

### Post by mlind on 2006-06-17
fdisk and dd are good. use dd if you need to make sure that data recovery is not possible.

---

### Post by astoltz on 2006-06-18
I've never used gparted but I believe it is a patitioning tool - not a formating tool.  Maybe it does formating too.  However, the command "mkfs" is usually used to format already existing partitions.  There are several varieties of mkfs depending on what type of filesystem you are trying to create: mkfs.ext3, mkfs.vfat, etc... (actually, they are links to the "real" format commands.  But mkfs.[whatever] is easier for me to remember).

Be sure to read the man pages first```
man mkfs.ext3
```

---

