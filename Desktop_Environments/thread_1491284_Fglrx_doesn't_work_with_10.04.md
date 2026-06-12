---
title: "Fglrx doesn't work with 10.04?"
date: 2010-05-23
forum: Desktop Environments
---

### Post by lurreluck on 2010-05-23
Hi, I just installed Kubuntu 10.04 and I am experiencing problems with the fglrx diplay driver.

I installed it with Jocky and rebooted.
Everything works fine. But everything is so un-smooth. Like dragging & resizing windows.
It's not updating instantly.
It was smooth before installing fglrx but then I couldn't boot without nomodeset.
I am using a widescreen LCD monitor.

My xorg.conf
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:8:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

---

### Post by JCoster on 2010-05-23
When you say unsmooth do you mean that there is a lag of a second or so after you choose to maximise a window or open a new one etc.?

If so, this is a known issue and you must install a patch (read [this](http://ubuntuforums.org/archive/index.php/t-1172875.html)).

Note that this only occurs with Compiz switched on, so verify that it's smooth without Compiz in order to check that this is the cause.

---

### Post by JCoster on 2010-05-23
Also, I just realised this is in the Kubuntu forums so the above probably doesn't apply for you (without Compiz?).
Sorry..

---

