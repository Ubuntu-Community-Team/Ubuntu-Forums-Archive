---
title: "Help Duke Nukem Atomic Edition Installer Linux"
date: 2005-10-01
forum: Gaming &amp; Leisure
---

### Post by rmckay on 2005-10-01
Hi I finally got the installer to run but then this is what happened
> ryan@LinuxBox:~$ ~/Desktop/duke3d_atomic_edition-x86.run
Verifying archive integrity... All good.
Uncompressing Duke Nukem 3D: Atomic Edition for Linux........................... ..............................
/home/ryan/.setup10408: error while loading shared libraries: libgtk-1.2.so.0: c annot open shared object file: No such file or directory
ryan@LinuxBox:~$ ~/Desktop/duke3d_atomic_edition-x86.run
Verifying archive integrity... All good.
Uncompressing Duke Nukem 3D: Atomic Edition for Linux.........................................................
/home/ryan/.setup10485: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
ryan@LinuxBox:~$
ryan@LinuxBox:~$
ryan@LinuxBox:~$

So can you help?...

---

### Post by brk3 on 2005-10-01
Yes. Quite easy: open up synaptic and install the gtk1.2 librarys. done.

---

