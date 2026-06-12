---
title: "Wacom Intuos 3 ignoring Threshold option"
date: 2007-04-07
forum: Desktop Environments
---

### Post by phatotis on 2007-04-07
Hiya,

My Wacom Intuos 3 4x6 is working fine on my Ubuntu Edgy installation. A little compiling with the sources from linuxwacom.sourceforge.net and all is well. Working fine in the Gimp and Inkscape. My only problem is the ' Option  "Threshold"  "20"' line in the xorg.conf file has no effect. I've tried other values and nothing works. 

Here's the relative snipit from my file:

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
  Option        "Threshold"     "20"
EndSection

Anyone else have any experience with this. With my heavy hand it's hard to not keep constantly clicking the mouse through the stylus.

Thanks,
Phat] (*,)

---

### Post by kayosiii on 2008-01-04
I think I just figured this one out - head further down the xorg.conf file and you will see a part of the file that says uncomment these lines if you have a wacom tablet. - uncomment the lines

---

