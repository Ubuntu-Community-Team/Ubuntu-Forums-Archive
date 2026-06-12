---
title: "lightdm not Spanning Dual Monitors"
date: 2013-03-05
forum: Desktop Environments
---

### Post by TXTad on 2013-03-05
Howdy!

I recently installed 12.10 on my dual-monitor workstation and lightdm seemed to be aware of my dual monitors quite nicely, spanning across them. The greeter / login box would be on whichever screen had the mouse and the custom background for the highlighted user was correctly spanned across both monitors. At some point, it changed to simple mirrored behavior with the greeter on both screens and the dual screen wallpaper repeated separately on each monitor. I can't seem to find a setting or control that will change it back. I'm wondering if there was some update, maybe, that might have caused this, because I went as far as reinstalling the entire OS since I first noticed this problem after I installed every desktop environment I could find. I'm not back to nothing more than vanilla 12.10 with nothing else installed except for a few utilities unrelated to the desktop.

I would like to go back to the behavior of the greeter on only one monitor.

Tad

---

### Post by TXTad on 2013-03-07
Oddly enough, I have another system that is still working correctly.

---

### Post by TXTad on 2013-03-11
I have discovered that the greeter on only one monitor is only possible when using the proprietary nvidia drivers. When using nouveau or intel drivers, the greeter is mirrored on both monitors of a dual monitor setup. Does anyone know if there is any way around this limitation?

---

