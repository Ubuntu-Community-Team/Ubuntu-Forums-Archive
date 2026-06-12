---
title: "No monitor detection"
date: 2011-06-05
forum: Desktop Environments
---

### Post by paolo.quaglino on 2011-06-05
Hi,
after last automatic update it seems that my monitor cannot be detected, so I can choose only low resolution modes (800x600, 640x480)
Everything was fine until last week, I was using proprietary nVidia drivers, but now neither them nor ubuntu defaults seem to work

The only thing i noticed is that the settings app reads "unknown monitor" while i'm pretty sure it was correct before (both ubuntu and nvidia control panel)
I tried booting in recovery, making a new configuration, adding "modes" to /etc/X11/xorg.conf , downloading new drivers from nvidia..

any suggestions?
is there a way to roll back updates? i'm not sure what was done, is there a way to check? (or, best of all, a way to redetect everything like in a fresh install..)

thanks!

btw, my monitor is a Samsung Syncmaster 192v (1280x1024@60Hz, h: 31-81kHz, v: 56-75Hz)

---

### Post by paolo.quaglino on 2011-06-05
hi, solved by myself...
for anyone who may be interested in..

 - I simply removed every "nvidia" entry with synaptics
 - reboot in recovery mode (text mode-no gdm running!)
 - installed again the drivers downloaded from nvidia
 - had to add my video mode to xorg.conf and correct refresh rates: this unlocked the menu and now I can see every video mode
 - choose the correct mode with the nvidia utility

I post here just the "screen" section

Section "Screen"
auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_60 +0+0; 1152x864 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

