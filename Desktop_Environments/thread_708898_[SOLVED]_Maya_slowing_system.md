---
title: "[SOLVED] Maya slowing system"
date: 2008-02-26
forum: Desktop Environments
---

### Post by linuxpyro on 2008-02-26
I am running Ubuntu Studio 7.10 on an Intel Core 2 Quad machine with 2 GB of RAM.  I'm using the default environment, with Gnome, no compiz.  I have an nVidia GeForce 8500 GT, with the restricted drivers installed and direct rendering working fine.  Normally, the system runs quite well.

I use Autodesk Maya for 3D, though, and recently installed version 8.5 (this is a new workstation for me, so I had not run Maya on it yet).  When it starts up it runs fine for the most part.  The interface is relatively responsive in the main window.  The problem comes when I have to use something in Maya that opens a separate window.  That is, if I try to maximize the window after having minimized it the system hangs for about 10 or so seconds.  I can move the mouse, but that's about it.  No windows move, nor will their contents update.  After the 10 or seconds are up everything is fine again.  It's the same situation if I switch to a different workspace and then switch back to the one with Maya running.

I SSHed into this box and ran top.  This revealed that while these hangups happened CPU usage of Xorg peaked, hitting almost 100 % at one point, though typically it would hover around 50 % or so until the hangup ended.

Anyone have any ideas?

---

### Post by rapiscan on 2008-02-28
Have you considered inquiring with the Maya support?  I don't know if you have a legit copy of Maya, but this might be the best way to go for this type of problem.

---

### Post by linuxpyro on 2008-02-28
Yeah, I think I'm going to try that next.

---

### Post by linuxpyro on 2008-03-01
OK, I think I fixed it after seeking advise on Autodesk's forums.  I had to disable composite in xorg.conf.  You can do it by adding these lines to the end:

```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

I guess this means no Compiz, but oh well...  :(

---

