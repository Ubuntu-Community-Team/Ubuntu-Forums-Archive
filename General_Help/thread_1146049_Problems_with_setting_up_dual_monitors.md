---
title: "Problems with setting up dual monitors"
date: 2009-05-02
forum: General Help
---

### Post by Aseld on 2009-05-02
Hey all,

So I'm trying to set up dual monitors (NVidia GeForce 7950, Ubuntu Server 8.10 (with X11 and Openbox)) and am running into some problems. 

I know that there's an automated setup utility, but I don't want to install GNOME or KDE, and I understand that that's required. So I tried to do it manually via TwinView, but the NVidia installer tells me that it's not compatible with my kernel. 

I'm not really sure how to go about fixing this - any suggestions? 

Thanks a lot.

---

### Post by Aseld on 2009-05-03
...anyone?

---

### Post by theozzlives on 2009-05-03
It may just need to compile the kernel module.

---

### Post by alex_sv on 2009-05-03
AFAIK all you need to do is to properly modify your xorg.conf

I don't think that utilities will help to solve any particular problem, may be it would be better to read about xorg.conf...

I have the following configuration (simplest possible, I believe):

```

Section "Monitor"
    Identifier  "Monitor0"
    ModelName       "Dell Inspiron 1501 Monitor"
    Option      "DPMS"
EndSection

Section "Monitor"
    Identifier  "Monitor1"
    ModelName       "Samsung SyncMaster 960BG"
    HorizSync       30-81
    VertRefresh     56-76
EndSection

Section "Screen"
    Identifier  "Screen0"
    Monitor     "Monitor0"
    Device      "Radeon 200M"
    DefaultDepth    24
    SubSection "Display"
        Depth   24
        Modes   "1280x800"
        Virtual 2560 1024
    EndSubSection
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Device"
    Identifier  "Radeon 200M"
    Driver      "ati"
    BusID       "PCI:01:05:00"
    Option      "XAANoOffscreenPixmaps"
EndSection

```

---

### Post by Aseld on 2009-05-04
@alex: modifying xorg.conf won't help enable TwinView when I don't have the appropriate drivers.  

@theozzlives: it tried that, and said it couldn't find the appropriate module. If I have to install a new kernel, so be it - I just don't know which one (currently using the server kernel).

---

