---
title: "Can't get ubuntu to start today"
date: 2010-02-06
forum: Desktop Environments
---

### Post by greensaharatj on 2010-02-06
Last night I installed Ubuntu 9.10 32bit on my desktop alongside with windows 7 and everything was working fine I didn't make any major changes I just installed the nvidia driver for desktop effects and put a couple of applications like Wine and Compiz Fusion on for the desktop cube effect.  Now all of the sudden nothing will boot up from the bootloader I select Ubuntu and just get a black screen with the flashing curser.  I am fairly new to linux and am not familiar with the command line at all but is there a way to fix this? Is it possible that windows 7 is somehow interfering with my linux installation? Thanks!

---

### Post by Exp HP on 2010-02-06
It sounds like GNOME isn't displaying under the new drivers.  I wouldn't know how to fix it, but for now you can try this as a workaround:

Ctrl+Alt+F1 (this switches to the main console)
Ctrl+Alt+F7 (this switches back to GNOME)

Using those two key combinations in sequence essentially "refreshes" GNOME.  See if it helps or not.

---

