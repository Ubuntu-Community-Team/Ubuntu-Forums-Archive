---
title: "Various ATI Driver Issues"
date: 2011-11-11
forum: Desktop Environments
---

### Post by benjaminmorris on 2011-11-11
Edit: Found a solution that works for me. See the bottom of the post for more.

First off, the specs list:
Ubuntu 11.10 64bit
Radeon HD 5770 with FGLRX driver (if necessary)
Affected environments: Unity 3d, Gnome 3 (not classic)

Now the issues:
1. I believe the rest of these issues would go away if I could solve this one - when using the radeon driver instead of fglrx, my fan speed stays 100%. I've tried to search for ways to resolve just that, but haven't really found any good solutions. I'm no good at writing scripts, and I don't know the linux commands well enough to do much exploration myself, though I'm perfectly fine following instructions, running commands etc. If anyone knows of a good way to get the fan speed to auto-adjust like it's supposed to, that would be best for me, I think. If not, here are the other issues.

2. Unity 3D:
A. Lag - yes, this has been addressed. Yes, I've disabled vsync in CCSM and messed with vsync options in ATI CCC. Yes, I've disabled Detect Refresh Rate in CCSM as well. Over all it's fine, but it still doesn't feel quite as smooth as with the radeon driver. If anyone has any further tweaks to recommend, I'll gladly try them. Otherwise, it'll work as-is.

B. Windows not refreshing - This one I cannot live with. More often than not, when Alt-tabbing between windows, I'll come back to one and it will not refresh the view for anything. The only way to reset it is to maximize/restore it. Once done, it's clear that the window has been accepting all the input I gave it, just not refreshing its view. This occurs with the fglrx driver, not the radeon driver.

3. Gnome 3 - Again, in my searching I've come across this issue a couple times, but I have yet to find a straightforward solution. In Gnome 3, the top bar (what do they call it again?) is... well, here, have a screenshot:
[IMG]http://img831.imageshack.us/img831/9193/screenshotat20111110230.png[/IMG]

Various other elements in Gnome 3 are just as wonky. It also has a good bit of lag, just like Unity before the above-mentioned tweaks.

So, any takers on how to resolve these issues? Would sure be nice to a fully functioning, beautiful desktop for a change.

Sidenote: fixing either Unity or Gnome 3 is fine with me. I'm not really attached to either one.

Thanks everybody!

Edit: Found the solution for the fan speed on radeon driver. The trick is to set the Power Profile to something other than "default" (I'm using "auto" for now to see what happens).
The instructions are here: [http://www.overclock.net/t/731469/how-to-power-saving-with-the-radeon-driver](http://www.overclock.net/t/731469/how-to-power-saving-with-the-radeon-driver)
This doesn't stick on reboot, so to set it on startup, do what [this guy]("http://ubuntuforums.org/showthread.php?t=1806349") says and add it /etc/rc.local and all should be well. I'm not planning on doing much gaming on this system, and the desktop performance of the radeon driver seems on par with if not superior to the fglrx driver, without all of the weird glitches. I'm happy. :-)

---

### Post by typhoon_tip on 2011-11-11
Forget Gnome 3 and FGLRX:
[http://ati.cchtml.com/show_bug.cgi?id=99](http://ati.cchtml.com/show_bug.cgi?id=99)

The page will take a while to load... lol

Instead, with latest FGLRX from ATI Unity 3D is working like a charm with my Radeon HD 3400 on ThinkPad T400.

---

### Post by benjaminmorris on 2011-11-11
*Almost* all issues are sorted out in Unity. It's just the window refresh issues as noted in 2.B. That makes it unusable. But either way, the radeon driver is working just fine now that power management is set to auto instead of default.

---

