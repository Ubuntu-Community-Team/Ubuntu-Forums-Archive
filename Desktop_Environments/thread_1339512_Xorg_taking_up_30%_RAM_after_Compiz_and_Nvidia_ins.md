---
title: "Xorg taking up 30% RAM after Compiz and Nvidia installed."
date: 2009-11-27
forum: Desktop Environments
---

### Post by afrodeity on 2009-11-27
I have just installed a Geforce 8400 nvidia graphicsgraphics card with 512mb memory onboard.

The drivers downloaded, I set up compiz, everything was working nicely. Then I tried installing extra "unsupported" compiz modules using a [script]("http://forum.compiz.org/showthread.php?t=12012"). The install didn't go very well because of bandwidth and was interrupted.

I then tried to set up 3D graphics in Virtualbox and the system crashed and hot rebooted. When I rebooted, the CPU and RAM was maxed out and it started reinstalling the nvidia drivers. I then rebooted again from a cold start and things came back to normal, but now Xorg is taking up 30% of my RAM, ie 30% of 1GB which suggests a [memory leak or problem with the driver. ]("http://ubuntuforums.org/archive/index.php/t-579739.html")


Is there anyway to remove the nvidia drivers and reinstall them clean? I guess this is the only way to get my memory back?:P

---

### Post by Melcar on 2009-11-27
Are you running Compiz?  It's normal for X to eat up your RAM once you switch to composition.  I'm using KDE4 effects and it's not unusual for xorg to eat up as much as 500MB in a session.

---

### Post by afrodeity on 2009-11-27
Okay, solved this I think. Not such a biggy - I changed over from version 173 to version 185 of the nvidia driver by opening System > Administration > Hardware Drivers. The applet downloaded the newer driver and I set-up compiz again and Xorg appears to be a respectable 4% of memory.

If this option was not available I would have had to completely [remove nvidia and reinstall manually.]("http://ubuntuforums.org/showthread.php?t=1125400") as indicated in the first part of the how-to. 

The hardware application only allowed me to deselect the old nvidia driver after I had downloaded the newer version. Thankfully, the newer version works with my card.

So thanks to those who went ahead of me for thinking about this problem. I can't say I've ever experienced such an easy fix with a video card before in an obviously problematic situation (corrupted code).
:)

---

