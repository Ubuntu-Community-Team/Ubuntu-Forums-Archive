---
title: "Twinveiw and games/vmware problem."
date: 2007-01-24
forum: Desktop Environments
---

### Post by HIGHLIFE on 2007-01-24
When I launch full screen games like armyops or apps like vmware, they use both screens.  It is very annoying especially in games to have one half of the game on one screen and one on another.:mad:   Is there an app that will allow me to easily turn twinview off, or a command that will launch a program on only one screen?

---

### Post by oolunchbox on 2007-01-25
the "Screen" section of my xorg.conf looks like so:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "L70N"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "MetaModes" "1280x1024,1280x1024; 1280x1024,NULL"
    Option         "TwinViewOrientation" "RightOf"
    Option         "RenderAccel" "true"
#   Option         "AllowGLXWithComposite"      "true"
    Option 	   "AddARGBGLXVisuals" "True"
    Option 	   "DisableGLXRootClipping" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

```
I can only vouch for Steam games (Half-Life 2 and CS:S) but the ```
Option         "MetaModes" "1280x1024,1280x1024; 1280x1024,NULL"
```
line allows me to set the resolution to 1280X1024 instead of 2560X1024 by telling the driver to ignore the second monitor.  Using that line makes the left monitor the display and the right monitor is just black, optionally you could use  ```
Option         "MetaModes" "1280x1024,1280x1024; NULL,1280x1024"
``` and have the right monitor be the display and the left black.

Hope that helps.

---

