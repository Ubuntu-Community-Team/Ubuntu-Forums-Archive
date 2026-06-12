---
title: "slightly annoying behavior of matlab r2010a on my computer"
date: 2010-05-08
forum: Education &amp; Science
---

### Post by lethalfang on 2010-05-08
Every time I open Matlab R2010a, the splash screen appears at the proper place, but the windows always open on the next desktop/workplace. I'd always have to go to the next desktop/workplace.
Why is that? It's weird.

---

### Post by sbergman on 2010-06-17
it IS weird.... do you perhaps switch between desktops while Matlab is busy loading, ie from the time the splash screen appears to the time Matlab opens?

---

### Post by Warthaug on 2010-06-17
It is wierd, and does not happen on my 2010a.

Have you tried:
1) Disabling the spash screen?  I believe this is done by starting using
```
matlab -nosplash -desktop
```
2) Disabling compiz (i.e. no desktop cube, wobbly windows, etc)

Those may help, but never having experienced your problem I cannot say for sure if they will help.

Bryan

---

### Post by lethalfang on 2010-07-12
Apparently, I might've moved the MATLAB window, such that a small part of that window was onto the next desktop. So when I closed that MATLAB window, somehow MATLAB remembers to always open the window on the next desktop every time. 
Fixed the annoying issue by re-maximizing the windows properly.

---

