---
title: "Desktop Size Dual Monitors"
date: 2011-03-24
forum: Desktop Environments
---

### Post by pennstatebadboy on 2011-03-24
I have two identical 18 inch monitors. One is landscape (1280 x 1024), the other is portrait (1024 x 1280).

Both monitors display properly in their respective resolutions and orientations. Windows also maximize properly within each monitor.

However, the (virtual?) desktop size of the monitor in landscape (1280 x 1024) seems to be 1280 x 1280. This means that there is a space of 256 pixels above the top edge of the screen that I can't see. Things tend to get lost in this area.

How can I fix this so that the desktop space is 1280 x 1024?

---

### Post by pennstatebadboy on 2011-03-25
I should clarify that I'm using these monitors side-by-side as one big desktop (not mirrored).

Is this an issue with the Compiz settings? I see the following Outputs in CompizConfig "Display Settings":

1024x1280+1280+0
1280+1024+0+256

---

### Post by Krytarik on 2011-03-25
I'm afraid there is no actual solution for that. This is obviously one of the downsides of setting up such a virtual desktop. However, you may try to solve that by setting up a xorg.conf:
[http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors](http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors)
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)

Greetings.

---

### Post by pennstatebadboy on 2011-03-28
Fiddlesticks!

---

