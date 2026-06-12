---
title: "[SOLVED] Splash resolution issues"
date: 2008-12-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gizmo688 on 2008-12-25
Im having trouble with my splash screen on bootup. Im running 8.04LTS on an Inspiron 1420n.

The first part of the splash sequence where the progress bar is displayed shows up perfectly. The following splash where the Ubuntu picture is displayed right before login is all whack. 

Im assuming its not a console buffer thing since the first part of the splash routine works fine. My menu.lst is set where default is vga=791. The kernel doesnt have a "vga=#" set after the "quiet splash" part. I did try a few resolutions through this approach, but this of course messed with the progress bar portion of the bootup splash.

Anyone know how i can make the second part of the routine appear normal?

Edit: Does this have anything to do with '915 resolution' or 'xserver-xorg-video-intel'?

---

