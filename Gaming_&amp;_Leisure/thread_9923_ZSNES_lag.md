---
title: "ZSNES lag"
date: 2005-01-02
forum: Gaming &amp; Leisure
---

### Post by Quest-Master on 2005-01-02
So, I decided to have some fun with ZSNES, and played with it a bit.

It lagged incredibly in the beginning, with sound lagging many seconds behind as well as the graphics. I changed it to OpenGL and a different resolution and speeded up much more.

However, sound still lags a few seconds and the same for the graphics. I've tried many different resolutions and drivers as well as installing alsa-oss, but nothing's worked as of yet.

I can tell it is lagging because the ROM is running so much smoother on zsnes under Windows. :( I've tried snes9x as well, which runs even slower.

---

### Post by varunus on 2005-01-03
What method are you using for sound output?  Is it ALSA or ESD?  If you're using ALSA, you shouldn't have lag problems unless you're using DMIX, and these problems can be fixed by modifying a configuration file.  If you're using ESD, see if you can switch to ALSA in ZSNES...

Also, make sure to go to the howtos section and read the howto on how to make multiple programs play sound if they currently can't.

---

### Post by Quest-Master on 2005-01-03
I can't find the option to see whether I can choose ESD or ALSA. It's not under sound options :(

That MIGHT be the problem though.

---

### Post by Quest-Master on 2005-01-05
I've tried about every Linux SNES emulator.. all returning the same performance described above. :(

---

