---
title: "Xorg 2 processess running under system monitor?"
date: 2008-05-08
forum: Desktop Environments
---

### Post by esteckis on 2008-05-08
Sorry if this is in the wrong section.  I just have a question that I am curious about. I am trying to track down why my laptop uses 30% continuous resources and my desktop uses 8% resources with the same things running.  I opened system monitor and see that I have 2 Xorg running and both are using 80 MiB of memory.   I can put one to sleep with no ill effects on the system.  At first I thought 2 Xorg running was that I have 2 desktops on the same monitor.  I only use 1 monitor.  On system startup under System Monitor, are there supposed to be 2 Xorg processes running all the time?

Laptop Dell 6400 Intel duo 1.6 1gig ram ATI 1400 video
Desk   AMD 3600 1.6 ghz duo 2 gigs ram onboard ATI 1250 video shared memory

Using Hardy Heron  Both are sing the Restricted ATI driver

---

### Post by macaholic on 2008-05-08
As far as I know that is not normal behavior at all, when you have no other applications open, try killing one of the processes from a command line and see what happens.

---

### Post by esteckis on 2008-05-09
I checked my desktop to see what was running. There were no xorg's running when I checked under the system monitor. On the laptop I have special effects at normal and on the desktop I have special effects at none.  So I changed the desktop special effects to normal and then 2 Xorg process started.  Then I changed it back to none and shutdown and restarted the desktop. Even though special effects are none the 2 xorg processes still load now.  I still need to learn a lot more about Ubuntu. I just find it weird that my laptops resources are used a lot more.  I really don't need Compiz except for using the mouse to switch desktops with the scroll wheel (that option I like). If Ubuntu had that as a standard effect I would disable compiz.  

This thread can be deleted.

---

