---
title: "Resolution problems"
date: 2009-02-13
forum: General Help
---

### Post by williamwade on 2009-02-13
I just installed XUbuntu 8.10 on my PC after a year or two away from Linux.
At first the resolution was wrong but I figured I'd have to set up the NVidia drivers, Which I did.

Then when I went to the NVidia X settings, It said my monitor was CRT (It is not, It's a 19" 1280 x 1024 TFT) and that my current resolution was 1024 x 768 and gave me no option for my resolution. When I set the "panning option to 1280 x 1024, the image became much bigger than the screen.

Anyone know how to set my screen to its proper resolution.

---

### Post by williamwade on 2009-02-13
Can anyone help me?

---

### Post by williamwade on 2009-02-21
Nobody?

---

### Post by Miaxi on 2009-02-21
> **williamwade said:**
> Nobody?

Press escape when the message about booting into Grub comes up and use the option to fix xserver problems. 

If that doesn't work, sudo gedit /etc/X11/xorg.conf and edit it manually. (Backup first.) 

Example:

Section "Monitor"
#TFT screen
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
#nvidia card using an nvidia driver
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes   "1280x1024"
    EndSubSection
EndSection

If your settings look fine and the correct driver is getting loaded, just adding the modes line might suffice.

---

