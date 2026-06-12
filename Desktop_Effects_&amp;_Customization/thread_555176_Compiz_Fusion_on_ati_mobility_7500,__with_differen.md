---
title: "Compiz Fusion on ati mobility 7500,  with different issues"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by weekendli on 2007-09-19
Hey guys, 

I got a little different issue with ait mobility 7500 on my compiz fusion.  It looks like in most siutation, compiz just work out of the box with 7500. Here is the message I got:

**compiz --replace**
```
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

I wouldn't even find the identical error on google. Basically, I'm using the tradditional radeon driver with agpmode 4, and glx and dri module.  There are the 2 important session of my xorg file, hope it can be a little bit help. 

If anybody has a clue of what it goes wrong, please do let me know. Million of thanks. 

Cheers,

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

### Post by w4ett on 2007-09-20
I'm not a C-F kinda guy, but here is a list of search results with the same error....

[http://us.cypherbios.org/index.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=Fatal%3A+Failed+test%3A+texture_from_pixmap+support#1114](http://us.cypherbios.org/index.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=Fatal%3A+Failed+test%3A+texture_from_pixmap+support#1114)

Good Luck)

---

