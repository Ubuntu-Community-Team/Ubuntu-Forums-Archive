---
title: "Paragon NTFS for Linux"
date: 2005-12-17
forum: General Help
---

### Post by anonz123 on 2005-12-17
im trying to install the driver under: Fedora core 4 kernel : 2.6.11-1.1369_FC4.stk16.
do use the install.sh script they provide you have to have:

[B]-kernel soruces installed
-kernel headers installed[/B]

i have the kernel sources installed as i needed it to install the nvidea driver, its under /usr/src/kernels/2.6.11-1.1369_FC4.stk16-i686 and apparently that install.sh script checks somewhere else

on this topic [http://ubuntuforums.org/showthread.php?t=52285](http://ubuntuforums.org/showthread.php?t=52285) drigloi says 

> Problem is that install.sh expects things in some slightly different locations:

1. It searches kernel headers under /usr/src/linux-`uname -r` (linux-2.6.10-5-386) while Hoary stores these under /usr/src/linux-headers-`uname -r` (linux-headers-2.6.10-5-386 actually)
SOLUTION for this: create a "/usr/src/linux" symlink to /usr/src/linux-headers-2.6.10-5-386
Code:

sudo ln -s /usr/src/linux-headers-2.6.10-5-386 /usr/src/linux


2. It searches for kernel modules under /lib/modules/2.6.10 instead of Hoary's /lib/modules/2.6.10-5-386.
SOLUTION: create a "2.6.10" symlink to /lib/modules/2.6.10-5-386
Code:

sudo ln -s /lib/modules/2.6.10-5-386 /lib/modules/2.6.10


3. The script uses awk and expects it under /bin while Ubuntu has awk under /usr/bin
SOLUTION as you might found out by now: create "awk" symlink under /bin
Code:

sudo ln -s /usr/bin/awk /bin/awk

prob is i don't know how to create symlinks, and i can't find my kernel-headers

any help is grately apreciated,

thanks

---

### Post by anonz123 on 2005-12-22
no one?

---

