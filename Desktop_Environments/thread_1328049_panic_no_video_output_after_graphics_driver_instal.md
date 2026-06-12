---
title: "panic: no video output after graphics driver install"
date: 2009-11-16
forum: Desktop Environments
---

### Post by Ampi on 2009-11-16
Yesterday I tried installing AWN (Avant Navigator Window) and for that I needed also an composite manager. So I installed compiz-fusion, turned on Visual effects Normal and installed my graphics driver.

When I rebooted my screen now just stays black and my power button slowly blinks (as to letting me know something s wrong).

Then I thought if I reboot with the LiveCD I can remove all the above mentioned and start working again.
But the liveCD, apart from being slow, shows a lot of problems. Of course X doesn't work anymore but also the liveCD doesn't get any further then

```
[   399.698082] SQUASHFH error: Unable to read page, block 333a9ab, size 7b2c.

```

How do I repair my computer? I would really like to use it and I'm getting close to really stressing :(.

---

### Post by Ampi on 2009-11-16
Okay, I tried the recovery mode of an older kernel (recovery mode of current kernel froze).That got me into a root terminal. 
There I uninstalled compiz-fusion, awn and the xorg-video-ati driver.
When I rebooted again into the current kernel, I could back into Ubuntu.
So I am very happy.

But I am also guessing this is one of the last times I try to install compiz or awn.
The onboard ATI card jusst doesn't work, at least also not on Karmic... :(

---

