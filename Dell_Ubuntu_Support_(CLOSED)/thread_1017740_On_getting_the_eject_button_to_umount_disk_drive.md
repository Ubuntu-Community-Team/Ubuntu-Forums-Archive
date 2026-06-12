---
title: "On getting the eject button to umount disk drive"
date: 2008-12-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by alancanniff on 2008-12-21
Hello,
I have a Dell M1530 running ubuntu 8.04. When I use the eject button for the DVD drive the disk ejects but remains mounted. I have to manually umount the drive, which is a bit annoying. When I eject the disk by right clicking the desktop icon, the disk ejects and umounts as it should. Does anyone know how to resolve this issues?
Thanks,
Alan

---

### Post by wyrless2002 on 2009-02-16
I am currently searching for the same answer. I have the Dell XPS M1530, with Media Buttons.  What configuration file could be altered to send the instruction to unmount, then eject the dvd drive, using the hardware media buttons on the keyboard? Thanks in advance.
--Aaron

---

### Post by sdennie on 2009-02-18
I don't think it's possible to do this (assuming the button is the same as the XPS M1330 button).  The problem is that the button doesn't register as a keypress.  To see what I mean, run "xev" from a terminal and then mouse over to the little window.  Hit the stop button and you'll some text going by showing that a key was pressed.  Hit the eject button and you'll see nothing.

Having said that, a custom DSDT might be able to fix it but, a quick look through the source doesn't make it obvious how to do so.

---

