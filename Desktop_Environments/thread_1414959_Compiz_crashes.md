---
title: "Compiz crashes"
date: 2010-02-24
forum: Desktop Environments
---

### Post by poppo_g on 2010-02-24
I have a problem running compiz. Everytime about a minute after I started up my laptop, compiz crashes. I can manually restart compiz, but then also docky and gnome-panel crash so I have to restart those also. After this everything works fine untill the next time I restart Ubuntu. I think the problem is somewhere in the fact that I have an ATI graphics chip. Does anyone have a solution for this problem?

Below some output:

**************************************************
Output of compiz-check:
Gathering information about your system...

Distribution: Ubuntu 9.10
Desktop environment: GNOME
Graphics chip: ATI Technologies Inc Device 9712
Driver in use: fglrx
Rendering method: None

Checking if it's possible to run Compiz on your system... [SKIP]

Checking for hardware/setup problems... [SKIP]

At least one check had to be skipped:
Error: No rendering method in use (AIGLX, Xgl or Nvidia)

**************************************************
fglrxinfo:
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200
OpenGL version string: 1.4 (3.2.9551 Compatibility Profile Context)

**************************************************
xorg.conf:
Section "ServerLayout"
Identifier "amdcccle Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:1:5:0"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "Extensions"
Option "Composite" "1"
EndSection

Section "ServerFlags"
Option "AIGLX" "on"
EndSection

Section "DRI"
Mode 0666
EndSection

---

