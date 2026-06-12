---
title: "[SOLVED] Can't set background image with xcompmgr running"
date: 2008-11-23
forum: Desktop Environments
---

### Post by x1a4 on 2008-11-23
Hi,
I'm running an Xfce session without a desktop and Blackbox instead of XfWM.  I'm also running the X compositing manager: xcompmgr.  

I'm unable to set a background on the root window when xcompmgr is running.  When I kill it, the background image shows up, when I run it, the background is BlackBox's style colour without the image.  Setting rootCommand for the BlackBox style I'm using doesn't help.  I've tried fbsetbg, xsetroot, display, and bsetbg to set the background.  Obviously I can run a desktop and set the background that way but I'd rather not.  

Any ideas how I can set an image on the root window while xcompmgr is running?

Thank you.

---

### Post by x1a4 on 2008-11-23
Never mind.  hsetroot did the trick.

---

