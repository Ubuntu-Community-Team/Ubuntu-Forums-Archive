---
title: "Xorg with dual monitor for HD3200"
date: 2009-05-13
forum: Desktop Environments
---

### Post by intropedro on 2009-05-13
Hello,

I have a problem with Xorg. I have a motherboard MA78GM-s2H with integrated HD3200. My tv (37" full hd) by DVI and my TFT (19") by VGA.

I configureth xorg with (with driver fglrx):

```
>> sudo aticonfig --initial=dual-head --screen-layout=righ
```

And the xorg.conf file is:

```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-1"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
        Screen      1
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

I can see two desktop but when I open any thing in the TFT, the windows is opened in the TV. I will take two weeks and I can't know why it don't work.

Greetings

---

### Post by alfalfa31 on 2009-11-06
I don't use TV's typically, but add this under Section "Module"

```
Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection 
```

Let me know if that works

---

