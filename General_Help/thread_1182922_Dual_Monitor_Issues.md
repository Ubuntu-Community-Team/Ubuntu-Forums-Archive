---
title: "Dual Monitor Issues"
date: 2009-06-09
forum: General Help
---

### Post by seagullplayer77 on 2009-06-09
This thread is sort of a continuation of this one:

[http://ubuntuforums.org/showthread.php?t=1182505](http://ubuntuforums.org/showthread.php?t=1182505)

I was trying to figure out the problem with Opera and then I realized than in the nVidia Settings Manager, the monitors in my dual monitor setup were in the wrong order. I had set my laptop monitor (1440x900) to be on the right and my other monitor (1280x1024) to be on the left. Both monitors are set to be their own X environment (i.e. I am NOT using TwinView or Xinerama). When I checked the settings manager, however, my *laptop monitor* was on the right and my other monitor was on the left. I changed the order and went through the whole process of saving my settings to xorg.conf and restarting xserver, but the order of the monitors was still switched.

For whatever reason, Opera thinks that my laptop monitor is only 1280 pixels wide instead of 1440, so it doesn't load the right 160 pixels properly. And now, on my other monitor, there's a black bar at the bottom of the screen because it thinks it's only 900 pixels tall, not 1024.

I'm not really sure of the reason for the quirkiness, because all my other programs (Firefox, Thunderbird, Pigeon, OpenOffice.Org, etc.) work just fine on my laptop monitor and interpret it as being its proper size. I can't seem to get my settings to stay put, and it's really starting to bug me. I'm using the latest nVidia proprietary driver and I never encountered this problem when I was using Hardy.

Anyone have any ideas?

---

