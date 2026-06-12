---
title: "Overhead presentation with twinview."
date: 2009-02-21
forum: General Help
---

### Post by luisito on 2009-02-21
I have a laptop that I have used many times to give lectures with an overhead projector. I have Ubuntu 8.10 in it. It's a Dell Precision M4300 with an NVIDIA Quadro card and I installed the proprietary nvidia drivers.

The crt/lcd button in the keyboard works fine and clones the output to the secondary display. But the projector resolution doesn't match the lcd resulution and I get a virtual display larger than the actual display which is not good for a fullscreen presentation.

I found the twinview mode more practical. In this way my projector displays what is to the right of what my lcd monitor displays. I can put the presentation on the projector and  big clock on my lcd monitor. All great. What is the problem then?

The problem is how to tell an application that when it goes fullscreen it should go to the secondary display. It seems to work randomly for me. Adobe reader used to do it a few months ago, but after some update (not sure what) it doesn't anymore. It always goes fullscreen on my lcd monitor. On the other hand I can get Evince to go fullscreen on the projector by dragging it to the right and then setting it to fullscreen. So I can still give a basic presentation with Evince. But I would like to be able to use Adobe Reader (it can do cute animations with javascript that no other pdf reader shows appropriately).

Does anyone know how to make Adobe reader go fullscreen on the projector with twinview?

Here is the relevant part of my xorg.conf.

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [Quadro FX 360M]"
    Driver         "nvidia"
#    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [Quadro FX 360M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
#    SubSection     "Display"
#        Modes      "1280x800"
#    EndSubSection
    Option         "TwinView" "1"
    Option         "metamodes" "DFP: 1280x800 +0+0, CRT: 1024x768 +1280+0; DFP: 1280x800 +0+0, CRT: 800x600 +1280+0; DFP: 1280x800 +0+0, CRT: 640x480 +1280+0"    
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "nVidia Corporation G80 [Quadro FX 360M]"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP: 1280x800 +0+0, CRT: 1024x768 +1280+0"    
EndSection
```

---

