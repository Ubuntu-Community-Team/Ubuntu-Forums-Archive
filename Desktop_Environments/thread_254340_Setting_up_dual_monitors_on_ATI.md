---
title: "Setting up dual monitors on ATI?"
date: 2006-09-09
forum: Desktop Environments
---

### Post by winter_mute on 2006-09-09
I have a laptop, a Dell e1505, which has a port for a secondary monitor to be plugged into.  I'd like to set up a secondary monitor under linux -- preferably under Xgl/Compiz as well as linux! -- but all the guides I've seen for ATI w/ 3d rendering have given me no luck.  Here's my info:

Dell e1505
ATI Radeon Mobility x1400 w/ 256 MB Hypermemory
Laptop monitor runs at 1650x1050 max, and I'd prefer it to run at this size, but if the only way to get it running is to have a lesser resolution, I'm willing to sacrifice that much.
LCD I want to set up is running at 1440x900.

Any tips for what I should try to install here, or how I should set up my xorg.conf?  (Also, if anyone knows how to get your wallpaper to strech across both monitors in XP, I'd love to know how!)

---

### Post by wieman01 on 2006-09-09
I am using Xinerama to do just that... But there are pros & cons. The problem with Xinerama is that it does not support 3D acceleration but this is not needed in my case.

And yes, the wallpaper stretches across both screens (even on my Sony Vaio laptop). Try this link, it shows my latest xorg.conf that works. I am using Xinerama for my external projector.

[http://www.ubuntuforums.org/showthread.php?t=237640]("http://www.ubuntuforums.org/showthread.php?t=237640")

Please note that I am applying 2 different resolutions in this example. Simply change the resolution lines if you want to have the same resolution for both screen. But I guess you got the idea.

---

