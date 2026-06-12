---
title: "Mathematica 6.0 Plot3D, ListPlot3D, Graphics3D crashes, problems"
date: 2007-11-12
forum: Desktop Environments
---

### Post by mikesf on 2007-11-12
Mathematica 6.0 crashes on ubuntu 7.10 when you try to plot in three dimensions. 2-d plotting still works, but Plot3D, ListPlot3D, Graphics3D all crash. There is a simple solution by forcing Mathematica to use certain drivers. your start command should be
mathematica -mesa -defaultvisual
and it should work ok.

---

### Post by mikesf on 2007-11-15
so now it's crashing again, only this time it happens whenever i minimize a window. i got rid of the -defaultvisual switch and it seems to work now ... so it should be
mathematica -mesa

---

### Post by GreenFlash on 2008-02-08
Thanks mike, this seems to work.

---

### Post by Dionysios on 2008-04-05
It also worked for me. Thanks Mike!

---

