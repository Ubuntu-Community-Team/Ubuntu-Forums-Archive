---
title: "Mythtv (mythfrontend) startup"
date: 2005-09-07
forum: Desktop Environments
---

### Post by Chareos on 2005-09-07
Hi,

On my dual head setup I had to start a X server for LCD and another X server for TV. This gave me the required control about screen resolution and desktop extension.
My problem is that entries in ./kde/Autostart are processed twice (1 time each X server).

I managed to run mythfrontend on my tv using prefix DISPLAY=:0.1
(DISPLAY=:0.1 mythfrontend)

using the script
**if ! `pidof mythfrontend`; then DISPLAY=:0.1 mythfrontend ; fi**
mythfrontend gets started TWICE on the TV !


Does anybody know hot to run mythfrontend ONLY if no mythfrontend is already running ?


Many thanks

---

### Post by Chareos on 2005-09-09
no way?

---

