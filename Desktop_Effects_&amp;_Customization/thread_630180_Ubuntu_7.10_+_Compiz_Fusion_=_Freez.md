---
title: "Ubuntu 7.10 + Compiz Fusion = Freez"
date: 2007-12-03
forum: Desktop Effects &amp; Customization
---

### Post by inzaghi89 on 2007-12-03
Hi,
I've installed Compiz Fusion which is on cd with Ubuntu 7.10 and I've a problem...

Compiz have freezes... i can't do anything, mouse don't work, keyboard to. Pressing ctr+alt+backspace doesn't work to. I think it's Compiz bug, but i really don't know how to fix this.

My PC conf:
Ubuntu 7.10/compiz 1:0.6.0+git20071008-0ubuntu1.1
ram: 1gb ddr
graphic: nvidia gf 6600gt
processor: amd athlon xp 1800+@1540mHz.

Please for help, because i really like CF, and this bug is so aggravating.

---

### Post by ayampanggang on 2007-12-03
is it always happening or just sometimes?
what video driver are you using?

i know X had a bug where it sometimes freezes and only the mouse works. This was supposed to be fixed some while ago though.

Try 
```
glxinfo | grep direct
``` and see if it says "Direct Rendering: Yes".

and please post your /etc/X11/xorg.conf file, preferable the **Section "Device"** part (between **Section "Device"** and a few lines below until **Endsection**)

---

### Post by inzaghi89 on 2007-12-03
> **ayampanggang said:**
> is it always happening or just sometimes?
what video driver are you using?

i know X had a bug where it sometimes freezes and only the mouse works. This was supposed to be fixed some while ago though.

Try 
```
glxinfo | grep direct
``` and see if it says "Direct Rendering: Yes".

and please post your /etc/X11/xorg.conf file, preferable the **Section "Device"** part (between **Section "Device"** and a few lines below until **Endsection**)

It's always happened when i've active compiz fusion... always, but sometimes it's on the system start, sometimes after few hour...

I've nvidia-glx-new 100.14.19+2.6.22.4 - from synapic/installation ubuntu.

> inzaghi89@inzaghi89:~$ glxinfo | grep direct
direct rendering: Yes
inzaghi89@inzaghi89:~$

```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x1024_75 +0+0; nvidia-auto-select +0+0"
# Removed Option "metamodes" "1280x1024 +0+0; nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_75 +0+0; 1280x1024 +0+0"
EndSection
```

---

### Post by inzaghi89 on 2007-12-04
So? Could somebody help me?

---

### Post by Clarke on 2007-12-04
I have the very same problem. Computer freezes from time to time when compiz enabled.
Btw. My Video-card ist 6600gt too.

---

### Post by inzaghi89 on 2007-12-04
I think there is no way to fix this or nobody know how fix.

---

### Post by Clarke on 2007-12-21
Still no ideas about it? It's kinda not very comfartable when your system freezes regulary

---

