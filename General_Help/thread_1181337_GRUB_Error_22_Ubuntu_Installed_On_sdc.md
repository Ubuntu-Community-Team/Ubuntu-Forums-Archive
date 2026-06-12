---
title: "GRUB Error 22 Ubuntu Installed On sdc"
date: 2009-06-07
forum: General Help
---

### Post by MisterD2009 on 2009-06-07
I installed Ubuntu on the sdc drive of my desktop.  I also installed GRUB on the MBR of that drive.  I then changed the drive boot order so the sdc drive is polled first.  The boot screen came up, but when I selected the first entry, I got an error 22.  Is there any way to get this to work?  Thanks

---

### Post by ronparent on 2009-06-07
Yes.  

Shuffling the drives after a grub setup just confuses the former grub drive identities.

Boot from a live cd, open a terminal and load grub - **sudo grub**

At the grub prompt, enter the following series of commands:

**find /boot/grub/stage1**

enter the output from that as follows

**root (hdx,y)**

and then

**setup (hdx)**

The output from that last command should tell you if successful. You should then be able to boot to your install from the grub boot menu.

---

