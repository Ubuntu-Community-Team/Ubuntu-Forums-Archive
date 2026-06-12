---
title: "Starting x with a diffrent config?"
date: 2007-09-03
forum: Gaming &amp; Leisure
---

### Post by zzzzzZZZZzzz on 2007-09-03
Is it possible for me, as having dual monitors, start my third "game sandbox" X server in such a way as to have it read from a different "xorg.conf" file?

Any assistance is appreciated, though I suppose if there is no such solution I can just deal with the mouse running off the side of WoW and others. :-({|=

---

### Post by ZylGadis on 2007-09-03
There is just one xorg.conf, but you can specify different server layouts / screens / whatever in it. Then you can run startx with the respective layout / screen, which will solve your problem. I did a similar configuration on my laptop for when I need to force an external monitor / projector: by default it runs only the laptop screen, but I can pass -section "Cloned" to startx, and a new X session is started on both the laptop monitor and the external port.

man Xorg
man startx
man xorg.conf

are your friends.

---

