---
title: "getting the screensaver to work"
date: 2008-08-17
forum: Desktop Environments
---

### Post by geovino on 2008-08-17
I have the screensaver selected and set at 10 but it doesn't come on. what else is needed to get the screensaver to work? using xubuntu8.04

---

### Post by ZeldeR on 2008-08-17
Hallo, check your idle adjustments.

Your screensaver can come only when your machine is idle, maybe its your problem ??

screenshot:

---

### Post by jimmy the saint on 2008-08-17
gnome-screensaver is not set to run at startup by default. This causes a lot of issues with power settings as well, as the gnome power settings app requires it to function. See the link below for a step-by-step fix.

[http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

it is post # 7

---

### Post by Glw8z on 2008-08-18
You could also check the session at login. I think Xubuntu has *xclient-script* selected by default. This doesn't start the screensaver (except for a blank screen if I remember right), but when you choose *xfce 4-session*, this should be resolved. At least that's my experience.

---

### Post by geovino on 2008-08-20
> **ZeldeR said:**
> Hallo, check your idle adjustments.

Your screensaver can come only when your machine is idle, maybe its your problem ??

screenshot:

That is checked off.

I'll change the number of minutes until it comes on and see if that helps.

---

