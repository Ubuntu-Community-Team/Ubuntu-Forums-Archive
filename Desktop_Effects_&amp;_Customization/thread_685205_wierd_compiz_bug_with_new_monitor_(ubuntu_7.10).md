---
title: "wierd compiz bug with new monitor (ubuntu 7.10)"
date: 2008-02-01
forum: Desktop Effects &amp; Customization
---

### Post by billionmonkeys on 2008-02-01
I purchased a new flatscreen monitor to replace my old CRT and after installing it and getting the resolution set up, compiz no longer draws the window borders.  Not sure I understand why having a new monitor would cause this.

some details: old monitor: adi microscan 1600x1200 @ 75 hz
new monitor: 24" widescreen acer 1920x1200@60 hz

gfx card is an nvidia 7600GT AGP.

I had to shut off compiz entirely to get my window borders to come back.  no compiz settings enabled would work.

the (hopefully relevant sections) of my xorg.conf is below.  Ideas welcome.

Section "Device"
        Identifier      "Generic Video Card"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Option          "ConnectedMonitor" "DFP"
        Driver          "nvidia"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1920    1200
                Modes           "1920x1200@60"  "1680x1050@75"  "1680x1050@60" "1600x1024@60"   "1440x900@60"   "1440x900@75"   "1280x800@60"   "1280x768@75"  "1280x800@75"    "1280x720@60"   "1280x768@60"   "800x600@60"    "800x600@75"   "800x600@72"     "800x600@56"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
Section "ServerFlags"
EndSection

---

### Post by mbrush on 2008-02-02
I don't think it's an Xorg thing.  It sounds more like a Compiz thing. AFAIK X doesn't have anything to do with the windows borders.  I don't know much about Compiz, but could it be that it needs to be reconfigured or something for the new monitor?

As a last resort you could try reinstalling compiz

---

### Post by billionmonkeys on 2008-02-02
I tried messing around with the configuration using the 'advanced desktop settings affects' menu, turned everything off but when i enable it i still have the same problem.  I also tried reinstalling it and still have the same problem.

---

