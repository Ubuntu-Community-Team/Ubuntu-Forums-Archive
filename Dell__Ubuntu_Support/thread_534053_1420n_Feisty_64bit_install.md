---
title: "1420n Feisty 64bit install"
date: 2007-08-24
forum: Dell  Ubuntu Support
---

### Post by exsecant on 2007-08-24
I'm on a 1420n with the 1440x900 display

I believe that the pre-installed Ubuntu is 32bit, and would like to install the 64bit Feisty, but upon searching the forums I read that there were several issues with a fresh installation on the 1420n, notably with video drivers...

Does anyone have experience with a clean installation?

I tried to find a 3D driver for X3100 that supports 1440x900 resolution, with no success.

(I have minimal experience using Linux)

---

### Post by kuja on 2007-08-24
> **exsecant said:**
> I'm on a 1420n with the 1440x900 display

I believe that the pre-installed Ubuntu is 32bit, and would like to install the 64bit Feisty, but upon searching the forums I read that there were several issues with a fresh installation on the 1420n, notably with video drivers...

Does anyone have experience with a clean installation?

I tried to find a 3D driver for X3100 that supports 1440x900 resolution, with no success.

(I have minimal experience using Linux)
Even the vesa driver should be able to support the resolution (at least, I haven't had any trouble with it.

To get full support for the graphics card though, you have to upgrade at least some of your packages to Gutsy.

I'm not sure about the other issues though. I'm avoiding those for now.

---

### Post by exsecant on 2007-08-24
Would you know which packages?  and does the VESA driver support 3D?

---

### Post by iggykoopa on 2007-08-25
the guide for getting the correct drivers and packages from gutsy are here [http://ubuntuforums.org/showthread.php?t=506744&highlight=1420+desktop+effect](http://ubuntuforums.org/showthread.php?t=506744&highlight=1420+desktop+effect)
it is working pretty well for me, still a little buggy here and there but nothing too annoying. hope it works for you. oh also I'm running 32-bit but im assuming if you install the same packes 64-bit it should be fine.

---

### Post by exsecant on 2007-08-25
Feisty universe also has xserver-xorg-video-intel but it is not installed by default... is that the same as the driver at [intellinuxgraphics.org]("http://intellinuxgraphics.org")?  I've read that some people have had success with the intel drivers.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=509408") explaining very well how to fresh install to the 1420n... my question is, does it also apply to 64bit?

---

