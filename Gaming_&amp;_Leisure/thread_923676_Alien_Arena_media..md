---
title: "Alien Arena media."
date: 2008-09-18
forum: Gaming &amp; Leisure
---

### Post by Irritant on 2008-09-18
Hi guys/gals...

New version of the game is due in a few weeks...this summer has been the summer of code.  Alot of new rendering features, plus some gameplay stuff like antilag, reward system, weapon balance, etc.
 
[http://icculus.org/alienarena/rpa/media.html](http://icculus.org/alienarena/rpa/media.html)

---

### Post by J.K.Makowka on 2008-09-18
Nice new rendering features...Is the engine now completely fixed function free?
How about a OpenGL ES 2.0 renderer for a openpandora port?
[www.openpandora.org](www.openpandora.org)

---

### Post by Irritant on 2008-09-19
It's not completely GLSL, there are still some things done with fixed Opengl commands, and there are also fallbacks so that older cards can still run basic normalmapping effects(provided they have the CPU power).  Eventually, the goal is to have all advanced effects using GLSL.  That *could* happen in this release.  It certainly speeds things up for those with the GPU horsepower.  We did do a ton of optimizing though, to be a bit less drain on CPU in non GLSL cases.  The renderer was really gutted alot, which is really the beginning of some things happening with it.  Alot more changes are on the way.

As far as porting to the OpenPandora, I have no idea what that would entail, and would be difficult without actually owning one.  Heck, I'm *still* waiting on the guy doing our official MACOS port.

---

