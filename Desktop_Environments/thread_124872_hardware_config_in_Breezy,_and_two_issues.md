---
title: "hardware config in Breezy, and two issues"
date: 2006-02-02
forum: Desktop Environments
---

### Post by gigoguy on 2006-02-02
Just installed a fresh Breezy, and messed around with fglrx to get it to recognize my ATI X800 card.  The output that I got from lspci concerns me a bit though.  Seems that the majority of my components are unknown devices.  As a newbie I don't know if this is normal or not, but I'm happy to run around and tweak config files if I'm supposed to:

0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4a49
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4a69
0000:02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:02:09.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:02:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

I'm having only 2 serious issues at this point:
1) when I restart GNOME (CTRL-ALT-bksp), the system hard crashes.  Screen goes to black, no response from soft-off on the power button.  
2) any OpenGL display will result in a hard crash after an undetermined amount of time.  Screen will freeze with its display at time of crash, mouse and keyboard are locked.

fglrxinfo for the second one:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 PRO Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

Any help is greatly appreciated, and I'm happy to RT*M as long as somebody can point me towards the right M :-)

Cheers,
Gigoguy

---

