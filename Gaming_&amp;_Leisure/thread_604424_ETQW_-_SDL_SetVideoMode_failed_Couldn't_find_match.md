---
title: "ETQW - SDL_SetVideoMode failed: Couldn't find matching GLX visual"
date: 2007-11-06
forum: Gaming &amp; Leisure
---

### Post by stil on 2007-11-06
I'm sure this has something to do with my xorg.conf. After some playing I managed to break my config and xorg reverted to a failsafe. And herein lies the rub - ETQW loads with the failsafe config, not with my xorg conf after installing nvidia-glx and chaning the driver type from nv to nvidia. 

Do I need to set an appropriate resolution and refresh for ETQW to load into? 

This is confusing the heck outta me. :confused:

---

### Post by mbradlcu on 2007-11-12
humm, I'm not having this issue, here's my xorg section that may be of relevance:

> 
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
#    Driver         "vesa"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GS"
    Option  "AddARGBGLXVisuals" "True"
    Option  "DisableGLXRootClipping"    "True"
Option      "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

let me know if this dosen't fix it,, thanks


---

### Post by Sandlst on 2007-11-13
> Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
[COLOR="Red"]DefaultDepth 24[/COLOR]
SubSection "Display"
[COLOR="Red"]Depth 24[/COLOR]
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
I got the exact same error you did, check this part of your xorg.conf file to make sure the depth is set to 24; for some reason mine was set to 16  even though I have a nice video card, after changing it the game worked for me.

---

### Post by ekravche on 2008-04-20
> **Sandlst said:**
> I got the exact same error you did, check this part of your xorg.conf file to make sure the depth is set to 24; for some reason mine was set to 16  even though I have a nice video card, after changing it the game worked for me.

Gonna give this a try, maybe some of the games will work for me after I'll change the resolution.

---

### Post by Natanael on 2008-04-26
Try to reinstall restricted drivers for you graphic card - for me it worked.

---

### Post by Deo Favente on 2008-09-05
I'm having problems too, but not with whatever ETQW is. Restricted drivers? I have some intel chipset something like 945 or something, but whatever i download, nothing appears in system->admin->hardware drivers what do i do?

---

