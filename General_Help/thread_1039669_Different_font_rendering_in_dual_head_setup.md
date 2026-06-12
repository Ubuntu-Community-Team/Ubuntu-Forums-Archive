---
title: "Different font rendering in dual head setup"
date: 2009-01-14
forum: General Help
---

### Post by jjdelc on 2009-01-14
I have a dual head setup (Both LG Flatron wide), a 21" at 1650 and a 19" at 1440 running separate X screens and Fluxbox 1.1.1 (from source) as WM on Ubuntu intrepid, both monitors are hook to the same Nvidia card (01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1) ) using the "nvidia" driver.

This is my xorg.conf:
```
Section "Device"
    Identifier  "nvidia0"
    Boardname   "Nvidia GeForce8600"
    Busid       "PCI:1:0:0"
    Driver      "nvidia"
    Screen  0
    #Option     "NoLogo"    "True"
EndSection

Section "Device"
    Identifier  "nvidia1"
    Boardname   "Nvidia GeForce8600"
    Busid       "PCI:1:0:0"
    Driver      "nvidia"
    Screen  1
    #Option     "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier  "L226WTQ"
    Vendorname  "LG"
    Horizsync   80 - 93
    Vertrefresh 60 - 75
    Gamma   1.0
EndSection

Section "Monitor"
    Identifier  "L194WT"
    Vendorname  "LG"
    Horizsync   31.5-65.5
    Vertrefresh 56.0 - 65.0
    Gamma   1.0
EndSection

Section "Screen"
    Identifier  "screen0"
    Device      "nvidia0"
    Monitor     "L226WTQ"
    Defaultdepth    24
    SubSection "Display"
        Depth   24
        Modes       "1680x1050@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier  "screen1"
    Device      "nvidia1"
    Monitor     "L194WT"
    Defaultdepth    24
    SubSection "Display"
        Depth   24
        Modes       "1440x900@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
  screen 0 "screen0" 0 0
  screen 1 "screen1" RightOf "screen0"
EndSection
Section "Module"
    Load        "glx"
    Load        "v4l"
EndSection
Section "ServerFlags"
    Option      "Xinerama 0"
EndSection

```

And I am getting this font rendering:

[http://img55.imageshack.us/my.php?image=captura20090114152820nv5.png](http://img55.imageshack.us/my.php?image=captura20090114152820nv5.png) <- on the 21" 
and [http://img102.imageshack.us/my.php?image=captura20090114152816do6.png](http://img102.imageshack.us/my.php?image=captura20090114152816do6.png) on the 19" screen.

I'd like both to render the fonts as in the 19" 

I'm attaching my xdpyinfo result. Does anyone know how to tweak my Xorg so it renders uniformly?

---

