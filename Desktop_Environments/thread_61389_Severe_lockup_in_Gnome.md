---
title: "Severe lockup in Gnome"
date: 2005-08-31
forum: Desktop Environments
---

### Post by Erucolindo on 2005-08-31
My whole screen locks up for no apperent reason sometimes. The system does not response on any keytype or mouse movement. I guess the problem could be in either gnome itself, x.org or in the kernel. The only thing I have noticed acting strange beside the lockup itself is that after rebooting after a lockup the "enterprise volume management system" sometimes take several minutes starting. i guess it has someting to do with my partitions, but i have no datacoruption (root as ext3 and a swap and a data drive (ext2) on a seperat hard drive)

anyone have suggestions? i've tried some of the tips from others that experient lockups, but none have worked. Please help, i dont want to go back to windows..  :(

---

### Post by KingBahamut on 2005-08-31
Can you at least get to a terminal? Ctrl-Alt-f2?

---

### Post by Erucolindo on 2005-08-31
Nopp, not responding to any typ of command i try..

I figure that the problem may be that i feed the bootparm vga=792, i'm going to run without that for a while and se if it makes a difference.

Would nvidias official linux drivers make sence?

---

### Post by Erucolindo on 2005-09-02
changing or removing the vga option didn't change anything. However, i noticed that if i tured of azureus ubuntu was as stable as ever. Now, is it azureus or the java vm that is causing the lockup?

---

### Post by d1337 on 2005-09-02
Is this a new install or have you added / changed hardware just before this problem started?  I had sporadic lockups on my machine recently after a clean install.  After some digging, I made some changes in bios which seemd to remedy.  More specifically, I set AGP to 1X and toyed with Adavanced Power Management to give full control to the operating system.  This seemed to do the trick as it's been up all day today without a reboot (usually would lock every hour or so), but as always, YMMV.

Anything from dmesg or .xsession-errors?

d1337

---

### Post by Erucolindo on 2005-09-03
haven't checked them. have had no crash since i stoped using azureus, so that is definently the problem.

is there any way to fix that?

---

### Post by ~jaime on 2005-09-04
Azureus also freezes my system...

---

