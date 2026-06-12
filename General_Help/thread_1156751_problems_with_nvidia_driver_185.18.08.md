---
title: "problems with nvidia driver 185.18.08"
date: 2009-05-12
forum: General Help
---

### Post by mayankbhagya on 2009-05-12
s/m config:
nvidia 8400m gs            256 mb
Ubuntu 8.10

I installed the nvidia beta driver 180.xx . Then i installed mesa lib i.e libgl1-mesa-dev.deb . Everything worked and I got a simple opengl program working. Even glxgears was giving an output of 2000 fps.

i then wanted to install nvidia's cuda development files. The driver version 185.18.08.
After I did that, my X crashed! On reboot it gave an option to run in 'low graphics mode'.

I reconfigured the xorg.conf to use 'nv'.

I reinstalled nvidia driver using envyng but 'glxgears' is not working!
it gives:
Xlib: Extension "GLX" missing on display ":0.0"
GLX failure: couldn't get an RGB, Double-buffered visual

i'm unable to compile opengl programs!

Next i tried the nvidia driver 185.18.04.
My X crashed again!

PLZ HELP!!!

---

