---
title: "Wierd problems with xserver restarting and quake 4."
date: 2006-01-13
forum: Desktop Environments
---

### Post by Stork on 2006-01-13
This is semi gaming and semi other things, so I thought I should post it here instead of the gaming forum.

Every once in a while, quake 4 crashes, and I need to manually reboot. When I do reboot, xserver wont load, so I run in recovery mode. I then use 'sudo dpkg-reconfigure xserver-xorg' and pretty much hold down enter (:P) until it's configured, then I restart xserver and it works, but without my nvidia drivers.
So I open a terminal and do 'sudo apt-reconfigure nvidia-glx'. 
Then I use 'sudo dpkg-reconfigure xserver-xorg' again, and select 'nividia' instead of 'nv'. I then pretty much hold down enter again :P.

The curious thing is, it's the same way every time. Surely after I've change the settings they shouldn't change every time I manually reboot?

---

### Post by Stork on 2006-01-14
Well I tried doing a normal reboot with System > Log Out and I still need to re-change the settings.

---

### Post by Stork on 2006-01-14
Bump?

---

