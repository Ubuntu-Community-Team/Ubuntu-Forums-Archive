---
title: "torcs and billardgl problems probably freeglut3's fault"
date: 2006-07-27
forum: Gaming &amp; Leisure
---

### Post by fragmental on 2006-07-27
So, my system isn't the fastest system.  It has a 2200+ athlon pc100 memory and an ancient nvidia vanta 8 mb.  However, it should still be enough to run torcs and billardgl in 640x480 16bpp mode.  Tuxracer and neverball and some other opengl games run just fine.  Direct rendering works just fine.

However, torcs and billardgl do not run well at all.  They run well for a few seconds and then pause and then repeat ad infinum.  I checked the dependencies to see why it affected those games specifically and they both use the freeglut3 library, where I believe the other games do not.  Also, they both won't go full screen, which is a known bug with the freeglut3 library.  As far as I know, a bug that will never be fixed because development has stopped.

So, does anyone know any solution to the freeglut3 problem?

---

