---
title: "Dual Monitors, Fullscreen to current monior"
date: 2009-05-15
forum: Desktop Environments
---

### Post by d0ugal on 2009-05-15
I have dual screens working, however when I maximise a window it spans the full width of both screens. I tried enabling dual-heads but that means I can't move a window between monitors.

I'm not sure what setting I'm looking for?

I have an ATI HS 4870 with new drivers downloaded and run today.

Sorry if this answer is here, i wasn't sure what to search for... everything i found didn't seem to be what i want.

---

### Post by Nathan.Flow on 2009-05-15
> **d0ugal said:**
> I have dual screens working, however when I maximise a window it spans the full width of both screens. I tried enabling dual-heads but that means I can't move a window between monitors.

I'm not sure what setting I'm looking for?

I have an ATI HS 4870 with new drivers downloaded and run today.

Sorry if this answer is here, i wasn't sure what to search for... everything i found didn't seem to be what i want.

I believe some where where you have your desktop resolution set, you have it set so that the landscape it 2x of your original land scape..  Example... if your regular resolution is 1280X1024
you have yours set to 2560X1024 where the first number is the length of your desktop and the second number it the height. 

I'm currently trying to get my second monitor to display more than a X for the cursor.. can you post your xorg.conf so I can have a look... thanks.

---

### Post by d0ugal on 2009-05-15
The resolution already seems to be set to the two sizes combined... its working fine as two monitors but its acting like one big monitor.

This is generally fine but it means things fullscreen over two monitors. Most annoying when you fullscreen say a video as its split right down the middle and hard to watch.

```
Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
    SubSection "Display"
        Virtual   2560 1024
    EndSubSection
EndSection

```

---

### Post by d0ugal on 2009-05-19
So I managed to get dual-head working this the following xorg.conf

However its still not quite what I was hoping to archive. I now seem to have two totally individual desktops. I can't drag windows from one to the other for example.

Opening firefox in both just gives me an error that its already open...

I'm trying to create something between what I had before (all one desktop) - i think its called bigscreen and the dual-head.

Is this possible? Basically, all I want is big screen but when I go full-screen I want it to snap or stick to that window. Otherwise its particularly annoying when you try and do things like play video and its split over two screens.
 
Any thoughts, ideas or suggestions would be greatly appreciated.

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "Default Screen" 0 0
    Screen         "aticonfig-Screen[0]-1" RightOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
    SubSection "Display"
        Virtual   2560 1024
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

