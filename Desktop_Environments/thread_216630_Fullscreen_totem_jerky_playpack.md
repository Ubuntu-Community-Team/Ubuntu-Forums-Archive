---
title: "Fullscreen totem jerky playpack"
date: 2006-07-15
forum: Desktop Environments
---

### Post by starNIX on 2006-07-15
I am not sure but this bug has appeared recently.  When I play a video fullscreen in totem,  it plays fine until I move the mouse and the controls appear.  Then the video is jerky.  The audio plays fine.  

Once the controls disappear,  the video is smooth as silk again.

Any ideas?

---

### Post by starNIX on 2006-07-17
anyone?

---

### Post by starNIX on 2006-07-18
FYI it does it only with the "nvidia" driver.  Not with the "nv" driver.

Here are the pertinent parts of my xorg.conf

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NV17GL [Quadro4 200/400 NVS]"
    Driver        "nvidia"
    #BusID        "PCI:1:0:0"
    VideoRam    65536
    Option         "RenderAccel"         "true"
EndSection

Section "Monitor"
    Identifier    "Sony GDMFW900"
    Option        "DPMS"
    HorizSync     30-121
    VertRefresh     48-160
    Modeline "1920x1200" 237.000 1920 1936 2096 2528 1200 1201 1204 1250
EndSection

Does that help any?

---

### Post by starNIX on 2006-07-18
AHHAAA!!!  I figured it out.  I forgot that i changed the video driver in totem_config to "OpenGL" for use with XGL but I never changed it back when I quit using XGL.

Now that i changed it back to "Auto" its smooth as silk...

---

