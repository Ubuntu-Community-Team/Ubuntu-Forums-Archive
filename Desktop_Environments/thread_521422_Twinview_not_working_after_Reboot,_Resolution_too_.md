---
title: "Twinview not working after Reboot, Resolution too high"
date: 2007-08-09
forum: Desktop Environments
---

### Post by kaitsobato on 2007-08-09
Hello :)

well since yesterday i'm using ubuntu ^^
Ok graphicsdrivers are installed (NVIDIA 100.14.xx)

I'm using 2x 30" Displays with 2560x1600 native Resolution each, using a Dual-DualDVI NVidia Card and i want to use, of course, Multimonitorsetup.

So, with the Nvidia settings everything works, i can apply the changes, and Twinview works for me. Xinerama works perfectly but i want to use Beryl which does not work with Xinerama (RandR failed.. with Option "RandR "yes" there is only one screen affected by beryl and i cannot move Windows from left to right...)

BUT after restarting GDM cannot be started because the Resolution is too high and he can't find proper modes.. 

Upon bootup (and X crashing) there is an error saying 

> (II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP-0:2560x1600_60+0+0,DFP-1:2560x1600_60+2560+0"
(II) NVIDIA(0): Virtual screen size determined to be 5120 x 1600
(WW) NVIDIA(0): Virtual screen width of 5120 pixels is too large; clamping to
(WW) NVIDIA(0):     4096
(WW) NVIDIA(0): Mode "DFP-0:2560x1600_60+0+0,DFP-1:2560x1600_60+2560+0" is
(WW) NVIDIA(0):     larger than virtual size 4096 x 1600; discarding mode
(EE) NVIDIA(0): Failure to construct a valid mode list: no modes remaining.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Since i really want to use Twinview+Beryl and me being a total newby i don't know what i should do to make this work :-/ I mean: it works after applying it in gnome, why not after reboot? :(

---

