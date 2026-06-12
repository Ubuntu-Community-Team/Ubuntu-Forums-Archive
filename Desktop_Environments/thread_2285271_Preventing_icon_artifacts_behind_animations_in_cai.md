---
title: "Preventing icon artifacts behind animations in cairo-dock"
date: 2015-07-04
forum: Desktop Environments
---

### Post by Lars Noodén on 2015-07-04
Cairo-dock is leaving artifacts of the icons.  The original icon is left in the original place in the background of the dock even if the icons have been modified or displaced by active and ongoing animation. See the attached screenshot. The expected results would be that there are no artifacts behind the active animations.  See the attached cropped screenshot.   I've tried with OpenGL and without, and both states cause the artifacts.  How do I get clean animations and prevent the artifacts?

---

### Post by kerry_s on 2015-07-04
vid card ?

---

### Post by Lars Noodén on 2015-07-04
C79 [GeForce 9400] Nvidia.  It seems to be using the nouveau driver.  The artifacts are not present on other accounts on the same machine.  I've tried erasing ~/.config/cairo-dock/ but that has had no apparent effect on them.

---

### Post by w201 on 2015-07-04
I once had a similar issue but found out I was running two instances of cairo-dock. Could this be the case with you?

---

### Post by Lars Noodén on 2015-07-05
Thanks, that was it.  More than one apparently:

```

$ pgrep -lf cairo-dock
2703 cairo-dock
2715 cairo-dock
2780 cairo-dock
2783 cairo-dock
2793 cairo-dock
2798 cairo-dock
2808 cairo-dock
2815 cairo-dock

```

killing all but one fixes the problem.  However I did not intentionally add more than one.  Something is wonky with the settings if it is possible to so easily have multiple docks launched at the same time.  I see that even if cairo-dock is launched at startup, there is still an option on it to "+ Launch Cairo-Dock on startup".  That's probably where I got it.

---

### Post by w201 on 2015-07-05
No problems mate. To be honest, I don't quite remember what fix I used to solve it back than as it was quite a while back. I don't use cairo-docks option to launch on startup, I  insure it starts up through the system settings in my desktop environment if that helps you out. Gnome tweak tools to be exact.

---

