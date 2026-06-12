---
title: "errors on starting compiz fusion after installation"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by weekendli on 2007-09-20
I got an error message when I try to start compiz fusion on my machine. It is
```
 compiz --replace

xset:  unable to open display ""
xdpyinfo:  unable to open display "".
xvinfo:  Unable to open display
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system. 
```

And then I try to verify my driver provide enough suppport to compiz, there are some test I have done. 
It looks like the driver support texture_from_pixmap.  Because my video card is ati 7500, so I have to use radeon driver. But I also a handful of people can make compiz fusion work with 7500 out of box. I don't know what' wrong with my settings. There is also a part of my xorg file to show you my configuration. 

Any suggestions?

```
glxinfo | grep rendering
direct rendering: Yes

glxinfo | grep texture_from_pixmap
GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
```

**xorg**
```
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "dbe"

        Load "GLcore"
        Load "radeon"
        Load "xtrap"
        Load "drm"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AGPMode" "4"
        Option          "RenderAccel" "true"
        Option          "AGPFastWrite" "true"
        Option          "EnablePageFlip" "True"
        Option          "UseInternalAGPGART" "no"
        Option          "backingstore" "true"
        Option          "AllowGLXWithComposite" "true"
EndSection
```

---

### Post by Vadi on 2007-09-22
Same card here, Compiz works fine. Try setting your xorg.conf to this (thought you only need the first four options really:

> Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
        Option "AGPMode"       "4"
        Option "AGPFastWrite" "true"
        Option "RenderAccel"   "on"
        Option "MonitorLayout" "LVDS, NONE"
	Option          "ColorTiling"   "on"
        Option          "EnablePageFlip"        "on"
EndSection

---

