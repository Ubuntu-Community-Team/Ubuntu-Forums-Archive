---
title: "White screen with Desktop Effects/Beryl"
date: 2007-06-07
forum: Desktop Effects &amp; Customization
---

### Post by Orochi on 2007-06-07
Whenever I try to run Desktop Effects or Beryl I get a white screen. With DE, I can press escape a few times to get back to my regular desktop. With Beryl I have to restart x11 with ctrl+alt+backspace. Also, when I'm running  Beryl, if I hold  ctrl+alt and drag the mouse around, I can see the cube rotating, just the main 4 sides are white (the top and bottom sides have the Beryl logo on them). 

I'm running on an Intel Extreme graphics card (855GM) with the new xorg intel driver (xserver-xorg-video-intel).

I've been researching this problem a bit, and several threads have suggested adding```
Option "AddARGBGLXVisuals"  "True"
``` to xorg.conf under the "Screen" section.  I've tried this, and it results in no change.

If anyone else knows how to fix this, I would very much appreciate it.

EDIT: After consulting the Beryl forums, I've found that setting your color depth to 16 instead of 24 fixes this problem. After changing this in xorg, everything seems to run fine, although I'm not sure if running in 16-bit mode is a bad thing?

---

