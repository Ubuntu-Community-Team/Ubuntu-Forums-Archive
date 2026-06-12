---
title: "Desktop effects on nVidia RIVA TNT2 M64"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by bwang on 2008-01-10
I can't enable desktop effects. 3D works fine, because all the screensavers work. Are desktop effects possible with this card?

---

### Post by warbread on 2008-01-11
Check to see if you have direct rendering:

glxinfo | grep direct

If no, then you can't. If yes, you might.

---

### Post by hwertz on 2008-01-11
Unfortunately, the TNT2 does not support desktop effects (I was just looking into this as I have a machine at work with a TNT2 in it.)  The nvidia-glx-legacy drivers (71.xx series) do not support a few of the OpenGL extensions (composite mainly I think) that desktop effects need.  So, you'll get working OpenGL  but no desktop effects :(

     The main nvidia-glx driver supports composite etc. but doesn't support a bunch of older nvidia cards.  The in-between driver 87.76 (which most distros don't have as a choice, you have to get it manually) supports desktop effects and supports a lot more cards than the current nvidia-glx, but still doesn't support TNT, TNT2, Geforce256, Geforce DDR, Geforce2 Ti/GTS/Pro/Ultra, or the Vanta.  I have this version on a Geforce4 MX440.

     You're not missing out on a lot -- the desktop effects are pretty but they are in fact pretty subtle.

Rock on! :guitar:

---

### Post by ozp on 2008-01-12
at least you have the driver installed

I have geforce2 GTS on K6-III and neither the restricted driver manager or Envy works

both blinks the screen before boot up and then an aplication comes up saying stuff about low resolution (vesa driver)

I cam make NV driver with 1400x900 (or 1440x900) resolution

but I want nvidia driver to see if the computer scrreen gets faster than with NV

I found this driver to download from nvidia 
71.86.01 x86

and there is another version 1.0-7185 IA32

are they both for Geforce2 series? 

IA32 works with K6 III ?


Also the computer is so slow that thakes days to perform a boot and reboot

I spent some weekends trying to make this work and there is few information on this forum about this configuration (Because its very old one)

---

### Post by 137001469 on 2008-02-04
> **bwang said:**
> I can't enable desktop effects. 3D works fine, because all the screensavers work. Are desktop effects possible with this card?

thangyou

---

