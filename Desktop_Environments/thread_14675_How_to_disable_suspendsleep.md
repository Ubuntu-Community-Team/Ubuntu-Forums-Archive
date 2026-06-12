---
title: "How to disable suspend/sleep?"
date: 2005-02-09
forum: Desktop Environments
---

### Post by bVork on 2005-02-09
Ubuntu has been hanging on me quite a bit. I think I've narrowed it down to the suspend/sleep functions, because it seems to happen if I either ignore my laptop for an hour or two or if I close the lid. Its certainly not a power issue, as my laptop is on AC power at all times.

So how do I disable the suspend/sleep functions completely?

---

### Post by rosslaird on 2005-02-09
Desktop --> Preferences --> Screensaver --> Advanced

---

### Post by bVork on 2005-02-10
I already tried that. It doesn't work. My screen still blanks and then hangs.

---

### Post by rosslaird on 2005-02-10
Try changing the settings in your xorg.conf file in /etc/X11 (or XF86Config-4, or whatever it's called if you have xfree instead of xorg.). Look for the DPMS settings (even try disabling DPMS if you want).

And maybe look at the guide [here](http://linuxreviews.org/howtos/power/xorg_dpms/).

All the power management settings for X programs (like Gnome) are set by the X server, so that will be the root of your problem.

---

