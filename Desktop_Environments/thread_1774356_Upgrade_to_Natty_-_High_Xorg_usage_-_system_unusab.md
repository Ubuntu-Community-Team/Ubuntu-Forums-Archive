---
title: "Upgrade to Natty - High Xorg usage - system unusable"
date: 2011-06-03
forum: Desktop Environments
---

### Post by 404wanderer on 2011-06-03
Hello all,

I've just upgraded my Mythbuntu box to Natty. Now I have a completely unusable system due to Xorg taking 70% of CPU. Mouse movement is possible and I can just type but that is about it. Using MythTv is impossible.

I'm running a standard mythtv build with the xfce desktop.
Anybody any ideas how to fix this one as it has rendered my PVR system impotent.

Cheers,
Wanderer

---

### Post by 404wanderer on 2011-06-11
OK, fixed.

Killed processes until CPU usage of Xorg dropped. Found out it was 'fuzzyflakes', the screensaver (even though screensaver wasn't currently activated).

Removed screensaver packages and that fixed problem.

---

