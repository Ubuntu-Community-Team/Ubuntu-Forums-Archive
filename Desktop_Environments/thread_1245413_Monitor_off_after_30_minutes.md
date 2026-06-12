---
title: "Monitor off after 30 minutes"
date: 2009-08-20
forum: Desktop Environments
---

### Post by soliko on 2009-08-20
Hi, 
My monitor turning off after 30 minutes with no activity even when after I disable the "Put display to sleep when inactive" in Power Management.
Is there other flag that I need to turn off?

---

### Post by enli on 2009-08-20
Try System > Preferences > Screensaver.

That was the source of monitor turning off in my case.

---

### Post by soliko on 2009-08-21
That is the problem, the "Power Management" that you get from the System->Preferences->Screensaver not working for me...

---

### Post by johnsdagg on 2009-08-21
after updating to 2.6.28-15-generic kernel my gnome power-management apparently does not work at all. changing any setting within it does nothing but i can still set things using 
# xset
commands. dpms is on etc.  use
# xset q 
to see current settings.
can set suspend time etc. using xset commands... can not do so using gnome power-management - anybody know what the deal is here? is it the kernel update?

---

### Post by soliko on 2009-08-22
Actually I updated the kernel as well mine is 2.6.30...

---

