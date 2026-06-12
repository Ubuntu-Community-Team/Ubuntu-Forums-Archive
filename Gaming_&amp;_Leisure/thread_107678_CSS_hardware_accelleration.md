---
title: "CS:S hardware accelleration?"
date: 2005-12-23
forum: Gaming &amp; Leisure
---

### Post by TrinitronX on 2005-12-23
After working to get Steam running under cvswine, I can now run steam without many problems.  I'm able to install and run games, however when I start up CS:S, it seems that it's emulating directX 9 through software... leading to an insanely low framerate and bad/choppy graphics.  It's really bad, and makes it unplayable.
I'm using an ATI 9800pro card, with the proprietary ATI fglrx drivers.  I can run fgl_glxgears fine, and the gl screensavers are able to use my hardware as well.
I managed to get into the options menu of CS:S, and saw that it's detecting a harware level of directX 8.1, but it's still set to use software for directx 9.
Is there any way I can force it into directX 8.1 mode?

I've tried running the game with the -dxlevel 81 flag, but it doesn't have any effect. (I did this through right clicking the game in steam, and setting it through the advanced run options for CS:S)

Or... alternatively, is there any way to get cvswine to somehow use directx 9?  I'm not sure if this is possible due to the card I'm using... but this option would be preferable if possible.

---

