---
title: "Dell 3007wfp 2560x1600 Black Screen"
date: 2008-04-02
forum: Dell  Ubuntu Support
---

### Post by cb9fl on 2008-04-02
I have a Dell Optiplex running an ATI Radeon HD 2400 XT. That is connected via DVI to a Dell 3007wfp.

Ubuntu 7.10 and 8.04 install correctly but default to 1280x800. I want to utilize the max resolution of 2560x1600 but every time I try to set the resolution that high the screen goes black.

Is it possible to run Ubuntu at 2560x1600?

Help please...

---

### Post by ridgeland on 2008-04-05
From Dell's site about the monitor:
Horizontal scan range  	49.31 kHz and 98.71 kHz (automatic)
Vertical scan range 	60 Hz
Optimal preset resolution 	2560 x 1600 at 60 Hz

You might check /etc/X11/xorg and make sure you have the right horizontal and vertical range.

---

