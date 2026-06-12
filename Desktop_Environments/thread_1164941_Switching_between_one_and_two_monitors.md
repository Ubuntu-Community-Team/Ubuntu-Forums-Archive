---
title: "Switching between one and two monitors"
date: 2009-05-20
forum: Desktop Environments
---

### Post by rkrd on 2009-05-20
This might be a question for the KDE guys, but I'm hoping that someone in here got this working, so here goes.
I recently installed ubuntu / kubuntu 9.04 on my MacBook Pro, and immediately got dual monitors working using the nvidia-settings tool using TwinView. So far so good. Since it's a laptop, I often disconnect the external monitor and use only the built in one (when travelling etc). Now, when in Mac OS X, the desktop automatically adjusts for this change, so that any stuff put on the external monitor space is moved to the built in screen. This includes the main menu bar so that the external monitor can be used ad the primary monitor while attached. When the external monitor is attached again, the previous layout is restored, which results in a seamless experience. However, when using KDE, all the things I move to the external monitor space (panels, desktop widgtes, icons) stays there, and are not visible anymore when disconnecting the external monitor. So far I haven't been able to figure out how to access the things I moved when running on the built in monitor only.

Has anyone had the same problem? Are there any solutions out there? Does Gnome handle this better?

---

### Post by cmreigrut on 2009-06-09
Anyone have any input on this?  I have basically the same problem.  I have an laptop with an NVIDIA card, a 1920x1200 lcd display and a 1920x1200 external monitor.  Since TwinView automagically sets up a virtual 3840x1200 desktop, when I boot up without the external monitor I still end up with a giant virtual display.  

Is there any way to get back to a single 1920x1200 display without restarting the NVIDIA settings, reconfiguring everything, and restarting X?

---

### Post by cmreigrut on 2009-06-12
I solved this by changing my metamodes to:
```
Option         "metamodes" "CRT: 1920x1200 +0+0, DFP: 1920x1200 +1920+0; CRT: NULL, DFP: 1920x1200 +0+0"
```
in xorg.conf

Now I can switch between 3840x1200 and 1920x1200 in krandr

---

