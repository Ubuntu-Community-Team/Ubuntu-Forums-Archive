---
title: "NVIDIA Drive 8756"
date: 2006-05-15
forum: Desktop Environments
---

### Post by Catacomb on 2006-05-15
Ok, I Have Tryed Everything, X Just Hangs! System Is Responsive (SSH, FTP, Ect..)
System:
Os: Ubuntu 5.10
P4 HT 3.0Ghz 800FSB
1 GIG OCZ EL Platinum Ram
MIS Neo3 M/B
XFX GForce 6600 256MB Dual DVI AGP
SB Aug-2 Platinum

Kernel 2.6.16.16 With SMP And HT Support And Junk Removed :-D 
Linux catacomb 2.6.16.16-p4+ht+v3 #1 SMP PREEMPT Mon May 15 19:56:38 EDT 2006 i686 GNU/Linux

Need Anything Else? I've Done EVERY Thing I Have Found With Out Success, Help. ](*,)

Even Nvidia Linux Guys Are Stumped
[http://www.nvnews.net/vbulletin/showthread.php?p=890184#post890184](http://www.nvnews.net/vbulletin/showthread.php?p=890184#post890184)

---

### Post by megamister on 2006-05-15
Verify your monitor refresh rates are accurate in your /etc/X11/xorg.conf  That had me hangin for about a day after install. Google to get your monitor specs and then compare, just a thought.

---

### Post by Catacomb on 2006-05-15
Monitor Norwood Micro m19bbk 19" LCD DVI

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 79.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nv"
    BusID          "PCI:01:00:0"
    VendorName     "Nvidia"
#    BoardName      "NVIDIA GeForce 6600"
    Option         "NvAGP" "2"
#    Option         "Coolbits" "1"
#    Option         "RenderAccel" "0"
#    Option         "CursorShadow" "1
    Option         "UseEdidFreqs" "FALSE"
    Option         "UseEDID" "FALSE"
    Option         "ModeValidation" "NoEdidModes"
EndSection

Nothing :(

---

### Post by Catacomb on 2006-05-15
Tweaking, Current Stage, Status: BAD!

```

Section "Monitor"
    Identifier     "Generic Monitor"
#    VenderName     "Norwood Micro"
    ModelName      "LCD-19"
    HorizSync       30.0 - 80.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
    Modeline       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066
    Option         "ExactModeTimingsDVI" "boolean"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nv"
    BusID          "PCI:01:00:0"
    VendorName     "Nvidia"
    BoardName      "NVIDIA GeForce 6600"
    Option         "NvAGP" "2"
    Option         "Coolbits" "1"
    Option         "RenderAccel" "0"
    Option         "CursorShadow" "1
    Option         "UseEdidFreqs" "FALSE"
    Option         "UseEDID" "FALSE"
    Option         "ModeValidation" "NoEdidModes"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by Catacomb on 2006-05-15
Sigh... All I Want To Do Is Be Able To Play UT2003

---

### Post by tseliot on 2006-05-16
Try removing the word "splash" from the kernel line in your /boot/grub/menu.lst

Then reboot and see if anything changes

---

