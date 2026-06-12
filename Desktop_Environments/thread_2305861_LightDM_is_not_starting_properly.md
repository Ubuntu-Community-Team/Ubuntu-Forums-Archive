---
title: "LightDM is not starting properly"
date: 2015-12-09
forum: Desktop Environments
---

### Post by Joseph_Tortorello on 2015-12-09
Whenever I boot my computer up, LightDM seems to start, but not completely. The mouse cursor (with the proper theme) appears, but it's on top of the console. If I switch to another terminal and do ```
sudo service lightdm restart
``` it starts up normally. Anyone know what might be going on and how to fix it?

---

### Post by T.J. on 2015-12-11
Try* sudo dpkg-reconfigure lightdm*  

Forcing the package to reconfigure may fix it.

Sounds like the display manager setup is a bit mangled.  How that happened I have no idea - it shouldn't, but if you are using 15.04 or 15.10 you should not expect stable behavior. Back around 2013, it was recommended that if you want predictable day to day performance that you use an LTS version.  The other releases are more "bleeding edge" and get far less testing and support.

---

