---
title: "Upgrading free ati driver"
date: 2008-12-30
forum: General Help
---

### Post by Zannax on 2008-12-30
Hello, I have an old PC with an ATI 7000VE video card: proprietary drivers don't support it so I'm using the free ATI drivers (xf86-video-ati ver. 6.7.195)

I've had some problems with it, tough (corrupted graphics in some videogames, glitches with compiz...).
So, I was wondering if it was possible to upgrade the ati driver to the newest version (6.9.0.91) which I downloaded from: [http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/refs/](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/refs/)

Is it possible/advisable?

I tried to unzip it, run the autogen.sh script provided and do "make" but there's no makefile...

---

### Post by Zannax on 2008-12-31
Some package needed for compiling were missing ("xorg-dev" and some other) so  the configure script failed...

After installing the required packages the new driver compiled and installed fine... Anyway even with the updated driver the glitches in the graphics remain... :-(

---

