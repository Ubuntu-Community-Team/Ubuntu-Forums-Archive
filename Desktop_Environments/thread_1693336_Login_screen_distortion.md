---
title: "Login screen distortion"
date: 2011-02-22
forum: Desktop Environments
---

### Post by Peter Beringer on 2011-02-22
Hi guys

I'm not sure if this is exactly the right thread

I have been running 10.04 quite successfully for about 12 months and I've now encountered a problem I can't solve.  

The login screen has become quite distorted.  It is divided in half with two cursors one half has half the login screen zoomed to about double size.  Instead of the normal sound play, it plays a distorted voice.  When I can log in into GNOME it's completely normal. If I switch users the login screen becomes two halves of black and white.  I thought it might be a desktop environment choice problem, but I cannot access the right side of the screen so I can't tell.  My login screen preference is set to GNOME.  

Thanks 

Peter

---

### Post by Krytarik on 2011-02-23
> **pcolamar said:**
> Ok, I found the problem.
My 3 years old boy had activated some zoom option of the "Universal Access Preferences" available in the lower left part of the GDM login screen that transforms the left part of the screen in a magnifier lens !

> **stinkeye said:**
> ```
sudo -u gdm gconftool-2  /desktop/gnome/applications/at/screen_magnifier_enabled --type bool  --set false
```Will turn the magnifier off at the gdm screen.
[http://ubuntuforums.org/showthread.php?t=1545815](http://ubuntuforums.org/showthread.php?t=1545815)

Grettings.

---

### Post by Peter Beringer on 2011-02-28
Thanks for that it worked a treat
Peter

---

