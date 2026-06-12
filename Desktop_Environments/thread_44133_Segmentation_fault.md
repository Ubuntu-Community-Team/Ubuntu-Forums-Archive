---
title: "Segmentation fault"
date: 2005-06-24
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2005-06-24
Whenever I launch glob2 (the game globulation 2) or d4x (downloader for x) I get an error 'segmentation fault'. Actually glob 2 is more precise, reporting

Toolkit : Initialized : Graphic Context created
Toolkit : Screen set to 1024x768 at 32 bpp in fullscreen
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

What does this mean? Is there a way to make them work? I should add that d4x previously worked, while I never tried Globulation2.
Thank you a lot
Andrea

---

### Post by elvis on 2005-06-24
It looks like SDL is having dramas trying to create a screen at that res and colour depth.

Have you tried upgrading (or downgrading) SDL?  I had huge problems with SDL 1.2.8 which broke most of my games and emulation software.  I dropped back to 1.2.7 and all was well.

"sdl-config --version" should tell you what version you have installed, as will Synaptic.

---

### Post by Nonno Bassotto on 2005-06-25
Synaptic says I have installed
libsdl1.2debian
libsdl1.2debian-oss
both in version "1.2.7+1.2.8cvs2041007-3ubuntu4", and some other items beginning with libsdl, but different version number, so i guess you refer to the main packages. I'm not able to force older version of these packages, since the menu item "Force version" is grey. I must say that this happens for the vast majority of the packages, so I don't know exactly how to restore an older version.

---

