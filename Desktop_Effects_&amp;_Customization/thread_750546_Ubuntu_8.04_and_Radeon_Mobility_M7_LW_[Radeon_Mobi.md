---
title: "Ubuntu 8.04 and Radeon Mobility M7 LW [Radeon Mobility 7500]"
date: 2008-04-09
forum: Desktop Effects &amp; Customization
---

### Post by wilsonB on 2008-04-09
End goal is to get Compiz Beryl up and running..I assume getting the drivers installed and working with gl is first thing to do.

Someone familiar with this video chipset please post instructions.

I can't even get my notebook graphics drivers to work.
Radeon Mobility M7 LW [Radeon Mobility 7500]
Tried a few things..
I have installed fglrx driver set from package manager. 
I ran; aticonfig --initial
edited my xorg.conf
tried many different additions;
driver="ati", "radeon", "fglrx" '
they are in my driver folder.

It just works with Generic video drivers..

Heres;part of  my xorg.conf

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Driver "radeon"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection


Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection


Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
Option "AIGLX" "true"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "enable"
EndSection

---

