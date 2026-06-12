---
title: "FCE Ultra Video Performance Issues"
date: 2007-07-24
forum: Gaming &amp; Leisure
---

### Post by Cosmonot on 2007-07-24
I just set up a new computer and I wanted to transfer over my emulators for some good old-fashioned gaming excitement. I've encountered a problem when I put my FCE Ultra on the new computer. The video has slowed down dramatically. My SNES and Genesis emulators still work fine, but the FCE plays very slow. If I shrink the gaming window down it speeds up to normal, but it seems like the bigger I make the window the slower it gets. I've never had this problem on any of the computers I've put FCE on, and I was wondering if anyone out there might know what has caused this problem and what exactly I can do to fix it (aside from playing on a smaller window, that is). Any help would be appreciated.

---

### Post by DoktorSeven on 2007-07-25
If you have direct rendering enabled for X, use the **-opengl 1** commandline option (or the Video->Enable OpenGL Rendering option in gfceu) to speed things up; it will use direct rendering instead of software rendering, speeding things up.

---

### Post by Cosmonot on 2007-08-01
Fantastic, I'll give it a shot. Sounds crazy enough to work  :-D

---

