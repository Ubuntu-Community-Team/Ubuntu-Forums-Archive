---
title: "Huge Slowdown After Installing Video Card"
date: 2008-12-12
forum: General Help
---

### Post by Umenzi on 2008-12-12
A few days ago I installed the ATI Radeon X1300, after several weeks of being sick of low-graphics mode, since my onboard graphics are the unsupported nVidia GeForce series. There was some wrestling involved in getting the driver working. Eventually I installed the driver downloaded directly from ATI's site.

The problem is that my computer has slowed down significantly since adding the X1300. There are hangs at random moments that last for several seconds, and when I click links or open programs, or even open menus, things grind to a halt temporarily. The music playing in the background will cut out, and then return as if it was never paused. Videos I have just clicked to will seem to fast forward through the first several seconds. The CPU isn't even working at 100% when this is happening. This happens at every screen resolution and refresh rate.

What the heck is going on?

My system:
Ubuntu Intrepid
AMD Athlon XP 3000+
768 MB RAM
(emachine desktop t3092, about 4.5 years old).

---

### Post by Chainz on 2008-12-12
I have something similar:

After enabling ATI proprietary drivers (for my ATI Radeon HD3450 AGP) and restarting (just Xorg using CTRL+ALT+BACKSPACE, or whole system just once) everything works perfect - fast and smooth, compiz and everything.

After another system restart, just after logging into the system it gets extremely slow.

Somehow CPU, no matter what I do, gets maximum up to 50% load, the rest seems to be taken by IOWait - that's at least what System Monitor says, mouse moves with lags (like freezing for half a second after every 1 second), and everything is so slow (even letters typed in terminal show up with few second delay), compiz turned off.

It was the same on Hardy and now on Intrepid (also different kernels on Hardy), no matter if I created driver packages from ATI binaries or just simply enabled them through Ubuntu Hardware Drivers applet.

Of course after disabling proprietary drivers everything is fine and smooth (no acceleration though), CPU gets to 100% normally and no IOWaits can be observed.

Join: [https://bugs.launchpad.net/ubuntu/+bug/292317](https://bugs.launchpad.net/ubuntu/+bug/292317)

---

### Post by Umenzi on 2008-12-20
All right, I have been completely unable to stop these hangs through any amount of troubleshooting.
I have installed the binary drivers from ATI's website -- how do I uninstall this and get something that will work correctly, if not in 3d?

---

### Post by Chainz on 2008-12-22
Some people managed to get it work, see here: 
[http://ubuntuforums.org/showthread.php?t=902913&page=2]("http://ubuntuforums.org/showthread.php?t=902913&page=2")

---

