---
title: "Fan control"
date: 2008-12-11
forum: General Help
---

### Post by pylon42 on 2008-12-11
This problem seems to be plaguing me... I've installed 8.04 and 8.10 on a 3 different laptops and 3 different desktop computers now. All completely different hardware and all seem to have a similar issue with fan control.

The cpu fan (definitely not the gpu fan) cranks up to max speed for a random burst, then drops down to almost nothing. Over and over and over again. It never stops and it doesn't matter what's running. I've unsuccessfully tried to install lm-sensors...

I don't care if I damage my hardware - is there some way to simply say: "Fan: you stay at this speed exactly, no matter what."
?

---

### Post by Hoyland84 on 2008-12-23
What happens if you open Synaptic, and search for lm-sensors? Can you find it, and if so, are you not able to install it?

You can try have a look at your BIOS setup and see if there's any way to adjust the fan. If not, this thread helped me out a lot:

[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

Took quite a lot of work for a newbie like myself, but I now have good control over my fan speed. Mine would just run at a constant full speed until i ran pwmconfig and did the right adjustments.

---

