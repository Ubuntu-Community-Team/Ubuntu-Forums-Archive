---
title: "Ubuntu 11 - Neverwinter Nights - Failed to initialize graphics"
date: 2011-05-29
forum: Gaming &amp; Leisure
---

### Post by Golevel on 2011-05-29
When I run nwn from terminal, here's what I get:

> Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Failed to initialize graphics.

My /nwn folder is in my /home/jason(user) directory

Here's the content of /home/jason/nwn/nwn

```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH

./nwmain $@
```

Here's LSPCI

> 00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)


I've already googled just about every combination I can think of but all of the fixes appear to be for nvidia. Any ideas?

---

### Post by Golevel on 2011-05-29
Just a heads up, I solved this by removing all nvidia packages via synaptic.

---

