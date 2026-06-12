---
title: "Let's find a way to get ATI drivers (free and non-free) fast enough to be usable!"
date: 2008-12-15
forum: General Help
---

### Post by Mazza558 on 2008-12-15
**The Problem**

[LIST]
[*]ATI drivers, both free and non-free, are often too slow compared to how fast they should be.
[*]A lot of users report that with either driver, 2D rendering is appallingly slow, even if 3D performance is fine.
[*]Other users have reported that even fallback drivers such as vesa are much faster.
[*]There is no single solution to this problem at the moment - let's see if we can find one.
[/LIST]

**The Solution**

- This is what we need to figure out. I reckon the main method will be to add certain Xorg options for certain configurations in other to give the drivers that extra boost.

---

### Post by Mazza558 on 2008-12-15
Okay, for the Open Source driver users, try adding this to xorg.conf, under the "device" section:

>         Option          "AccelMethod" "EXA"

---

