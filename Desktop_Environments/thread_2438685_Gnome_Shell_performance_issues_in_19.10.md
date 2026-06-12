---
title: "Gnome Shell performance issues in 19.10"
date: 2020-03-16
forum: Desktop Environments
---

### Post by teel on 2020-03-16
Hi,
I just installelled Gnome Shell in place of previously used KDE Plasma and I experience lots of performance issues.
Everything works good until I run some CPU-consuming process, then my mouse starts lagging, interface becomes intermittently unresponsive.
I started wondering if it's maybe Wayland issue (I guess Kubuntu uses old Xorg) and the way it utilizes graphic card and that maybe some gfx processing goes through the CPU and not the GPU.

My hardware is EliteBook 840 with i5 and Intel HD 5500 graphics card.

The glxgears gives 58 FPS which is probably a very bad result. What can I look at? This is not that poor hardware after all.

---

### Post by mc4man on 2020-03-16
Try gnome-shell (ubuntu session) in xorg which is the default.
Improvements are being made, focus would be on 20.04, you'll likely see better doing a fresh install of 20.04 when it releases or whenever you want to try it.  

(- I've both 18.04 & 20.04 though only occasionally log into gnome-shell, can't say I've seen as bad as you describe though.
Maybe open System settings > Details and make sure your your not on llvmpipe

---

### Post by teel on 2020-03-17
Thanks, will try it out.
In the meantime
```
$ glxinfo|egrep "OpenGL vendor|OpenGL renderer"
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 5500 (Broadwell GT2) 

```
so I should be ok.

---

