---
title: "graphic drivers not supported"
date: 2007-10-21
forum: Dell  Ubuntu Support
---

### Post by vsayikiran on 2007-10-21
my laptop is dell d520 latitude version. i installed a fresh copy of gutsy. previously i was using fiesty and everything was fine then. but afer installing gusty i am able to login properly into my pc. when i try to login it shows graphics not supported. i am using intel 950 gma card. my pc is having 1gb ram intel duo core processor and intel 945gm chipset
  this is the output of glxgears

error; couldnt get rgb double buffer visual
xlib: extension glx missing on display


output of glx info

name of display: :0.0

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by dacap06 on 2007-10-28
This sounds like you are running an unaccelerated X-windows server, or at least one that is not a good match for the i945 display.  Did you set your screen resolution, refresh rate, and graphics card?  If not, you need to do so now.  I believe [**this screen shot**]("http://www.ubuntu.com/files/GutsyImages/Screen-and-Graphic-Preferences.jpg") shows the proper place to do it in Ubuntu Gutsy.

If you already have done the card and screen setup or don't see your display on the list, then make sure you have the xorg-video-i810 server package installed.  This package provides the best driver for the Intel i8xx and i9xx family of chipsets, including i810, i815, i830, i845, i855, i865, i915, and i945 series chips.

If you have it installed already, then you may have to edit /etc/X11/xorg.conf to tell it to use the i810 server as the driver for your display.  Be sure to save an unmodified copy of xorg.conf first in case you screw it up (which is easy to do when editing manually).

---

