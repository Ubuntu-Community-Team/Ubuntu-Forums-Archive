---
title: "Warcraft 3 TFT - Wine - Ubuntu 8.04 - ATI, AMD"
date: 2009-02-04
forum: General Help
---

### Post by beamish. on 2009-02-04
Hello!


*My System:*
OS: Ubuntu 8.04 (hardy)
Gnome: 2.22.3 (Ubuntu 2008-07-09)
Kernel: 2.6.24-23-generic
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
Mem: 2788 MiB

Wine: 1.0.0-1 
Visual Effects etc.: None

Graphics:
=> ATI Radeon HD 3300 Graphics 
=> Catalyst Center: 1.8
=> Driver Version: 8.47.3
=> OpenGL Version: 2.1.7412


*My Problem:*
Just like others I cannot manage to run Blizzards Warcraft III TFT. 
I tried: -opengl; windowmode using my screenresolution; varied windows-emulations (win 98, win XP, win ME).

"wine war3.exe -opengl" displays the following: 

[I]fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x990, disabling mixer
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering
fixme:win:EnumDisplayDevicesW ((null),0,0x32eca4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef88,0x00000000), stub![/I]

Result: Blackscreen / have to kill wc3 process.


I would be grateful for any help!!

---

### Post by beamish. on 2009-02-04
lspci -vvnn:

(...)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3300 Graphics [1002:9614] (prog-if 00 [VGA controller])
	Subsystem: Biostar Microtech Int'l Corp Unknown device [1565:0217]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at d000 [size=256]
	Region 2: Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
	Region 5: Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

(...)

---

### Post by beamish. on 2009-02-05
Hey folks - thanks!

---

### Post by binbash on 2009-02-05
Did you move/rename the movies folder?

---

