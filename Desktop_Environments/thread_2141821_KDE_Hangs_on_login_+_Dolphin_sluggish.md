---
title: "KDE Hangs on login + Dolphin sluggish"
date: 2013-05-03
forum: Desktop Environments
---

### Post by x-shaney-x on 2013-05-03
After booting and logging in my desktop is unusable for anything from 30 seconds to 3 minutes.  During this time my wi-fi is not connecting and the sound system doesn't seem to start (no volume control on panel and no desktop login melody).
If I log out then back in again, rather than a fresh boot, it is slightly different.  Wi-fi connects straight away but the sound system takes even longer to start and has gone up to 20 minutes without starting.
There has been one or two occasions when everything has worked as it should, wi-fi connects instantly and login sound plays after a couple of seconds but the next time I boot it hangs again.

Not sure if it's related but Dolphin is very sluggish.  Takes several seconds to launch and the ight click menu takes several seconds to appear.  

Aside from the above issues, the rest of the desktop performs fine, all desktop effects work and everything else runs fast and smooth.
I did wipe it out and do a fresh install and found the second time around, it had exactly the same problems.

Running on Intel hardware - Core i5 with Intel graphics only.

---

### Post by x-shaney-x on 2013-05-04
Tried deleting various config files and nothing helped so went ahead and deleted ~/.kde completely.
This solved the login/sound/kmix problem but not the dolphin issues.

After several reboots, kmix was behaving and everything was starting up ok so decided it was safe to get things to my liking again.
Only changed a few things (set menus to display in titlebar button and changed some fonts).  Next boot the kmix issue was back.

Deleted .kde again and everything was working again.  Tried altering a couple of different settings (turning off the blue window glow and added some launchers to the panel) and kmix problem is back again.

Went through this routine two more times, altering something different each time and soon as I reboot the problem keeps coming back again.
So it seems kmix works fine on a completely unaltered desktop but not if I do anything whatsoever to alter it.

---

