---
title: "Xorg nvidia problems"
date: 2005-10-14
forum: Desktop Environments
---

### Post by toadi on 2005-10-14
I installed the nvidia-glx stuff in 5.10, but my laptop has a 1920x1200 resolution.

When running with the opensource nv drivers I get this resolution but with the nvidia-glx drivers this is only 1600x1200.

Can some advice me? I looked in the /etx/X11/xorg.conf and the only resolution in there is 1920x1200

---

### Post by toadi on 2005-10-21
Well if no one answers I need to solve my own problems.

It seems that with the normal nv driver xorg doesn't need a modeline. If I don't put a modeline when using the nvidia driver the maximum resolution is onlu 1600x1400.

I solved this for my laptop with following modeline:

ModeLine "1920x1200" 162 1920 1984 2176 2480 1200 1201 1204 1250 +hsync +vsync

Problem solved ;)

---

