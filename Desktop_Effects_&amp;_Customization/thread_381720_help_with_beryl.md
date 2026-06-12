---
title: "help with beryl"
date: 2007-03-11
forum: Desktop Effects &amp; Customization
---

### Post by stooby on 2007-03-11
I've installed Ubuntu Ultimate Gamers Edition, and had great fun breaking and fixing things over the weekend!  :) 

This time, though, I can't seem to find the answer to my problems...

I've been having problems with my monitor settings, being only able to choose resolutions up to 1024x768. After several breaks, I got this working and am now running 1152x864

but, something I did while I was sorting out my resolution seems to have broken Beryl.

Whenever I try to run Beryl now (I don't have it running at startup) it appears to apply the settings to my windows, then closes and switches back to Metacity

any advice would be greatly appreciated right now

---

### Post by aidanr on 2007-03-11
if you could post the output of running ```
beryl-manager
``` from a terminal that might help

---

### Post by stooby on 2007-03-11
hi aidanr, thanks for replying... I got the following:

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options

** (beryl-manager:12509): WARNING **: Beryl caught deadly signal 11

```
so, the error looks pretty obvious now, but I'm still not sure what it's actually going on about!  :confused:

---

### Post by astoltz on 2007-03-11
You might want to check that the Default Color Depth is still at 24.  Interestingly, the Nvidia setting tool on my machine doesn't even offer 24 as a choice so if your's is the same, you'll have to edit /etc/X11/xorg.conf

---

### Post by stooby on 2007-03-11
> **astoltz said:**
> You might want to check that the Default Color Depth is still at 24.  Interestingly, the Nvidia setting tool on my machine doesn't even offer 24 as a choice so if your's is the same, you'll have to edit /etc/X11/xorg.conf

just checked the default colour depth. All looks fine:

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by astoltz on 2007-03-11
Hmmm, maybe I'm being fooled by the part of the beryl-manager message that says > beryl: No GLXFBConfig for default depth, falling back on visinfo.What version of the nvidia driver are you using?```
cat /proc/driver/nvidia/version
```

---

### Post by stooby on 2007-03-13
thanks for all your help.

When I got home the other day, I found that my son had decided to help. He reloaded Ubuntu from scratch!

So, I can't tell you what my nvidia driver was...

I now have a different problem, so will start another thread

---

### Post by steveneddy on 2007-03-16
> **stooby said:**
> thanks for all your help.

When I got home the other day, I found that my son had decided to help. He reloaded Ubuntu from scratch!

So, I can't tell you what my nvidia driver was...

I now have a different problem, so will start another thread

I was just getting into this thread. Oh well.

-SE

Someone please close this thread.

---

### Post by Family_Guy on 2007-03-16
I'm having a similar problem...

Here's the output when running beryl-manager.
```

*****
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a00105 to texture
beryl: core: Received winTypeAtom but unable to find the window for the event
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2a0010c to texture
beryl: No GLXFBConfig for depth 32

```

---

