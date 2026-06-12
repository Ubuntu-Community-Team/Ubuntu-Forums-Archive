---
title: "Suspend wedges GDM -- help!"
date: 2013-12-02
forum: Desktop Environments
---

### Post by wil-otolith on 2013-12-02
I've been a very happy Ubuntu user for many years, and worked my way past any number of problems, but I've never seen anything like this.

Recently I got a new machine and installed 12.04 Precise on it, and after some fiddling, it looked like everything was working fine.  I just tried the suspend function for the first time, and on wakeup, GDM was seriously wedged -- a window popped up saying "System Error" and gave a bunch of details.  I took screenshots -- I think it was a segfault thrown by simple-slave -- which I'll post as soon as I figure out how to get them off that machine and onto the backup machine that I'm using now.  (I clicked on the button to send an error report to Ubuntu.)

Now a reboot gets me to a low-res startup screen, saying "Ubuntu 12.04" and four dots that change from white to orange and back again, nothing more.  I can use ctl-alt-F1 to get a command line, log in there, and run "startx" and I get the X display (including TwinView on my two monitors), the cursor works, but there's no desktop manager, no Dash, no way to go further that I can see.  I've rebooted several times and this behavior isn't changing.

From the command line, I've tried using apt-get to remove and reinstall gdm, no difference.  I've tried removing gdm and telling it to use lightdm instead, no difference.  I have no idea what's going on.  Can anyone help?

---

### Post by wil-otolith on 2013-12-02
Here are screenshots of the error message.  I've never seen anything like this.

---

### Post by wil-otolith on 2013-12-08
More behavior tests:  it looks like every boot using lightdm followed by an install of GDM causes the error message.  Removal and reinstall of GDM without reboot causes no error message, but no desktop manager either.  Any help here at all folks?

---

