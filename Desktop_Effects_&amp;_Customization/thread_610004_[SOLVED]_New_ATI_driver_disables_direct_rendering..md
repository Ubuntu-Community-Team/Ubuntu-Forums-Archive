---
title: "[SOLVED] New ATI driver disables direct rendering."
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by dgrafix on 2007-11-11
Heres the story and im posting it both as a warning and a hope that someone has already worked it out. I Have a new Radeon mobility X2300 HD. I was really happy i got direct rendering first time when i installed gutsy (driver ?.36). After some dissapointment that compiz failed to start i tried to install the new driver (?.43). This stopped all direct rendering and made 3d apps run badly. Compiz starts but has a white screen.

Everyone seems to think installing XGL is a great fix for compiz, but the deal is with XGL it slows the machine right down (try glxgears on both with (xgl) / without(direct render:yes) and see the difference), and because i use 3d a lot this is not an option. It would be nice to turn on the FX occasionally to dazzle my vista zealot mates tho :) Plus i would find the cube useful when not doing any hi-end stuff.

To fix the direct rendering situation I used envy to roll back to ?.40 which seems to be the only solution for direct rendering for this card. There appears to be no way of getting ?.43 to support direct rendering.

I think people should be careful in their rush to get compiz working as it appears that the configurations required kill the 3D performance for games and other things, especially when XGL is installed (regardless of wether the fx are on or off)

This is a card specific post but may also apply to other ATI models. I reccommend getting "glxgears" results from both drivers and compare the difference.

---

### Post by Ub1476 on 2007-11-11
The .43 driver is the **only** driver which support AIGXL for newer ATI cards. You only use XGL with drivers which do not support AIGXL. However, the 8.42.3 driver (which support AIGXL(=no XGL)) is incredible unstable and give very poor performance for most ATI card. I really suggest everybody to just use the driver from Restricted Driver Manager until the next Ubuntu release (april).

Also, Compiz does not kill the performance for games, but it doesn't work to play games with XGL (not because of poor performance).

---

### Post by dgrafix on 2007-11-11
> The .43 driver is the only driver which support AIGXL for newer ATI cards.

Correct, but im talking about actual hardware accelerated direct rendering. Installing the latest version seems to dissable this on the X2300 and it reverts to mesa indirect all the time.
You are correct in that AIGLX is only available for .43 which is needed for the composite support for compiz. But im talking about direct hardware 3d support which doesnt require AIGLX.
.40 is the only one that gives me the direct rendering i need as .43 doesnt and i cannot seem to find a way to turn it on.

---

### Post by dgrafix on 2007-11-11
Seems ive managed to solve this. There must have been a problem when i installed .43 before over .39. I thought id give it one last try, this time upgrading the driver from .40 it now seems to work. Im getting direct render:yes and when i turn compiz on i no longer get the whitescreen :)

Another thing i changed (that may have made a difference) was it had named the device "generic video card" in xorg.conf (too new to bw recognised mabe?).  I copy and pasted the device name "ATI Radeon Mobility HD 2300" from glxinfo over the entry "generic video card". Not sure if this did it or if it was simply the difference between version stepping.

---

