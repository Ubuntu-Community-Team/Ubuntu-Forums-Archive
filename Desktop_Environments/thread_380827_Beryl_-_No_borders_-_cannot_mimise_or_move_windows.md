---
title: "Beryl - No borders - cannot mimise or move windows - SOLVED"
date: 2007-03-10
forum: Desktop Environments
---

### Post by craigc on 2007-03-10
Hi All,

When i ran Beryl i had no borders or "window decorations" so i could not move windows around the screen, minimise or close them etc.

After searching the Ubuntu forum for an hour or so i found this link which fixed my Beryl settings when running Beryl with nvidia drivers.

[http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631)

Hope it helps someone out too

Craig

---

### Post by pkslot on 2007-03-11
Hopefully, you've just made my day. It seems that i have that same excact problem, and i'll give this a try!

I'll let you know if it turns out ok.

---

### Post by pkslot on 2007-03-11
I had a little problem making my resolution 24 bit in my Nvidia Settings, so i opened up my xorg.conf file
> sudo gedit /etc/X11/xorg.conf

and changed the depths set to 16, to 24, manually.

> Section "Device"
    Identifier     "NVIDIA Corporation NV31 [GeForce FX 5600]"
    Driver         "nvidia"
    Option "AddARGBGLXVisuals" "True"	
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV31 [GeForce FX 5600]"
    Monitor        "siemens"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection



 Now it works like a dream :KS

Maybe i shoult tell that i'm using a GeForce FX 5600, if it's usefull to anybody!

I owe alberto milone a great thanks for his really great ENVY script, doing so, for all who's having trouble installing their nvidia or ATI cards, [this is the place you want to visit]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by GenuineHawkin on 2008-07-11
The link no longer seems to work, anyone able to remember what had to be done to fix the problem originally?

---

