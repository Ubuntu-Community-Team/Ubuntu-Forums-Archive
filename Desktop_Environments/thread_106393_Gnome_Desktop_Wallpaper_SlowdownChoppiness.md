---
title: "Gnome Desktop Wallpaper Slowdown/Choppiness"
date: 2005-12-20
forum: Desktop Environments
---

### Post by neurosis on 2005-12-20
Whenever I set a desktop wallpaper in Gnome, I find the icon selection box (ie: click and drag a square to select multiple icons) really choppy and slow. It's better w/ no desktop wallpaper set, but still a bit sluggish.

I recently came to Ubuntu from Gentoo Linux and have never experienced this before.

My NVidia drivers are installed and working (I can play 3D games, which perform quite well.)

Relevant info from /etc/X11/xorg.conf:

```

Section "Device"
        Identifier      "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
        Driver          "nvidia"
        Option "NoLogo" "1"
        Option "NvAGP" "1"
        Option "RenderAccel" "1"
        Option "Accel" "1"
        Option "CursorShadow" "0"
        Option "NoRenderExtension" "1"
        Option "AllowGLXWithComposite" "0"
        BusID           "PCI:1:0:0"
EndSection

```

Running an Athlon XP 1800+, 768MB RAM, using the 2.6.12-10-386 kernel (no custom compilation or anything -- maybe its a pre-emptiveness setting?)

Help appreciated!

---

### Post by neurosis on 2005-12-21
Managed to fix it myself - I commented out all the 'extra' Options (NvAGP, RenderAccel, etc), restarted X, and everything was smooth again!

Didn't bother to figure out which one it was, but I suspect 'RenderAccel' was the culprit.

Hopefully this helps someone else!

---

