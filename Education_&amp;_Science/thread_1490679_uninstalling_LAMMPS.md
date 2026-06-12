---
title: "uninstalling LAMMPS"
date: 2010-05-22
forum: Education &amp; Science
---

### Post by phillyj on 2010-05-22
Hi all, 
I'm new to linux and am using WUBI to run it. I installed LAMMPS according to the guide written by Yoshis88 ([http://ubuntuforums.org/showthread.php?t=1390490](http://ubuntuforums.org/showthread.php?t=1390490)). I need to remove it as I made a mistake (forgot to use a compile file that was required). I used the make.ubuntu file but when I use "make uninstall" I get an error ( "No rule to make target `uninstall'." )

Is it possible to remove it without having to find and remove the installed files one by one?

Thanks

---

### Post by gunksta on 2010-05-22
It doesn't sound like you want to remove it, you just want to correct your mistake. Can you add the missing files and compile and install again? The new version will over-write the current installation, leaving you with a working system.

---

### Post by Yoshis88 on 2011-03-02
Think hard about this.

Can you uninstall something that wasn't installed?

"make ubuntu" command only makes an executable that will work on the ubuntu machine.  It doesn't place the executable anywhere besides the LAMMPS directory you unpacked.  All traces of LAMMPS (aka uninstalling) are removed when you delete the directory.

In the event you want to redo the compilation, first "make clean-ubuntu", then make the changes you want, then "make ubuntu".

---

