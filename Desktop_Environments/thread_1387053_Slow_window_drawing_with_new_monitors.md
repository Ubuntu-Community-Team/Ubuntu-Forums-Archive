---
title: "Slow window drawing with new monitors"
date: 2010-01-21
forum: Desktop Environments
---

### Post by jsgarvin on 2010-01-21
I installed Karmic back in November.  At the time I had dual 19" displays, and easily got them working with the Nvidia drivers.  For Compiz, under System/Preferences/Appearance/Visual Effects, it was set to the default of "Normal".  All worked fine. No problems.

Then, I upgraded in mid December to dual 22" Wide Screen monitors and adjusted the X server settings to for the new resolution on the two monitors.

At that point, if I rebooted or logged out and back in, *usually* windows and menus would open or drag extremely sluggishly, and before long the computer would lock up.  If (before it locked up), I logged out and back in (usually just once, but sometimes repeatedly), the problem would eventually clear itself and everything would run great until the next time I logged out or rebooted.

I did some searching around for anybody else having similar issues and that's when I got the idea to turn off the Compiz Visual Effects.  That totally solved the problem.  Now, I never have slugging window issues.

What I find curious is that, when I had compiz turned on with the 19" monitors, with all other hardware and drivers being the same, all was fine, and even with the new monitors, eventually I was able to get things to run smoothly simply by logging out and back in.

I certainly don't need the Compiz visual effects turned on and am perfectly fine with them being turned off. However, I thought maybe somebody might have an idea of what's going on that would allow me to turn Compiz back on. Or, at the very least, maybe a detailed description of my experience might help any developers of Compiz and/or the NVidia drivers that stumble across it here make improvements.

---

