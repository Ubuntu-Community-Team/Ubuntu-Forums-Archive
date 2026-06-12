---
title: "Boots to command"
date: 2006-01-19
forum: Desktop Environments
---

### Post by DrQuincy on 2006-01-19
I was trying to update my display drivers, etc and I inadvertantly set my machine to boot to the text command line.  How do I set it to boot back to graphics?  I understand there is a boot mode in a file somewhere but I don't know where it is.

Thanks.

---

### Post by az on 2006-01-19
You can boot into recovery mode.  You may need to press escape as you boot (read the screen) to display the grub menu.

In recovery mode

dpkg-reconfigure -phigh xserver-xorg

and then 

init 2

If that does not work, omit the -phigh switch to play around with settings...

---

### Post by DrQuincy on 2006-01-19
That has fixed it - thank you so much!

By the way, what does init 2 actually do?

---

### Post by az on 2006-01-19
Booting runs init scripts.  There are several runlevels.

runlevel one is for single user mode.  Fewer services get started in runlevel one.  This is what recovery mode is.

Runlevel two is the default multiuser runlevel.  It starts all the regular services that involve the desktop.

Runlevel zero is to shutdown and runlevel six is to reboot.

Init 2 means go into runlevel two.

You can go into a virtual console and run
sudo init 1
and you will end up in single user mode.

---

