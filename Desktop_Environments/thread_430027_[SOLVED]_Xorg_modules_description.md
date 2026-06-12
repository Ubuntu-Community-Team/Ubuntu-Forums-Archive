---
title: "[SOLVED] Xorg modules description ??"
date: 2007-05-01
forum: Desktop Environments
---

### Post by x1a4 on 2007-05-01
Hi,

Where can I find descriptions of the various Xorg modules installed in Feisty?  

Thank you.

---

### Post by wanchai on 2007-05-05
Good question. And which of these are really necessary and which ones can be turned off safely?

Here is something I found on [**http://wiki.x.org/wiki/XorgConfModulesSection**]("http://wiki.x.org/wiki/XorgConfModulesSection")
It's not as much as I expected from the "manufacturer's" website, but better than nothing.

```
Section "Module"
   # old bitmap font support (no longer needed as of xorg7.x)
   Load    "bitmap"
   # a collection of X protocol extensions that you want but shouldn't even be loadable
   Load    "extmod"
   # to load freetype fonts and type 1 fonts
   Load    "freetype"
   Load    "type1"
   # layer below vbe that emus x86 real mode so you can call into vbios
   # vesa bios interface for card setup stuff
   Load    "int10"
   Load    "vbe"
   # serial bus over which you speak the ddc protocol to get info from the monitor
   Load    "i2c"
   Load    "ddc"
   # direct rendering infrastructure which makes opengl go fast
   Load    "dri"
   # glx and glcore implement opengl
   Load    "glx"
   Load    "GLcore"
   # double buffering extension (no apps use?)
   #       Load    "dbe"
   # 1 of 3 extensions for application automation (unneeded -- most things use xtest from extmod)
   #       Load    "record"
EndSection

```

---

