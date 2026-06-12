---
title: "Gnome erroneously restores Title Bar"
date: 2010-12-21
forum: Desktop Environments
---

### Post by Clive McCarthy on 2010-12-21
This problem has had me stumped for a while. I'm writing an OpenGL full screen application using Glut (FreeGlut) which calls glutFullScreen().

If my program is called _directly_ then things behave correctly. If it called from a shell script then, after a few seconds, Gnome _sometimes_ erroneously restores the **Title Bar** to my program.

If I disable Gnome's Visual Effects then this problem is fixed.

System> Preferences> Appearance> Visual Effects> None :D

---

