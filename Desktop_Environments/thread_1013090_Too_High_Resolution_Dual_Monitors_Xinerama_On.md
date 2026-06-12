---
title: "Too High Resolution Dual Monitors Xinerama On"
date: 2008-12-16
forum: Desktop Environments
---

### Post by zeyt on 2008-12-16
Ok since hours of testing becase my xorg was empty on the instalation now im fine except for the reason that the 2 monitors resolutions is really high.

I cant change that on the preferences and i cant do anything.

I've tryed all but it doesnt work.

My Xorg.Conf is this made by me
```
Section "Device"
        Identifier      "Radeon 9000"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
        Driver          "ati"
        BusID           "PCI:0:9:0"
EndSection

Section "Monitor"
        Identifier      "19"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "17"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Primero"
        Device          "Radeon 9000"
        Monitor         "19"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280×1024" "1280×960" "1152×864" "1024×768" "800×600" "720×400" "640×480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Segundo"
        Device          "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
        Monitor         "17"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280×1024" "1280×960" "1152×864" "1024×768" "800×600" "720×400" "640×480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen	0	"Primero"
	Screen	1	"Segundo" RightOf "Primero"
	Option		"xinerama" "on"
	Option		"clone" "off"

EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
Section "DRI"
Mode 0666
EndSection
```

I want 2 monitors with 12xx or 1024 please.

Thank you all for reading and giving support.:KS

---

### Post by zeyt on 2008-12-16
Thank you for nothing. I've asked 2 questions in ubuntu forums and anybody answered. But i made it ...

For those poeple who are burning looking for a solution well mine was setting a virtual 1280 1024 at the xorg.conf in where the graphic card was (device)

---

