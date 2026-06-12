---
title: "Xgl segmentation fault"
date: 2006-06-03
forum: Desktop Environments
---

### Post by double0seven on 2006-06-03
hi, i installed xgl just the way its described in the howto, but when I start gdm it can't do so. when i try to start xgl manually by typing ```
sudo /usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
```
it gives an segmentation fault error.

any ideas what could be wrong? 


mfg doubleoseven

---

### Post by double0seven on 2006-06-03
does anyone have a similar problem or an idea how to solve this?

---

### Post by emuman on 2006-06-05
I have the same problem, but no solution yet.

---

### Post by double0seven on 2006-06-06
perhabs its not the cleanest solution, but now it works, i deleted all the packages necessary for X and reinstalled them, now it works.

---

