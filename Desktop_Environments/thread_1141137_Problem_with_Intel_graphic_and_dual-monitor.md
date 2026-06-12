---
title: "Problem with Intel graphic and dual-monitor"
date: 2009-04-28
forum: Desktop Environments
---

### Post by Raistlinbuntu on 2009-04-28
I have a problem trying the dual monitor with my Toshiba A10 laptop.

Just upgraded from 8.10 to 9.04, the external monitor (a 20" Dell) is recognized and mirror monitor works perfectly.
Both monitor (laptop and external) run at 1680x1050


The error in the Xorg.log is this one:
[I](EE) intel(0): Failed to pin front buffer: Cannot allocate memory

Fatal server error:
Couldn't bind memory for BO front buffer
[/I]

The video card is an intel integrated:

[I]00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
	Subsystem: Toshiba America Info Systems Device [1179:0006]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 2297
	Region 0: Memory at ff400000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at cff8 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
		Address: fee0300c  Data: 41b9
	Capabilities: [d0] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
[/I]

I tried both these configuration for the xorg.conf:
1: (automatically written by the "Screen resolution" tool)
[I]Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection[/I]

2: (written by me):
[I]Section "Monitor"
Identifier "Laptop Display"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Dell 20"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Primary Screen"
Monitor "Laptop Display"
Device "Configured Video Device"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1680x1050@60"
Virtual 3360 1050
EndSubSection
EndSection

Section "Screen"
Identifier "Secondary Screen"
Monitor "Dell 20"
Device "Configured Video Device"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1680x1050@60"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Primary Screen"
Screen "Secondary Screen" RightOf "Primary Screen"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection
[/I]

Can someone help me with this issue?
Thank you

---

### Post by Raistlinbuntu on 2009-04-28
Just a new info: if I disable compiz AND boot with the previous kernel (2.6.27), dual monitor works.

---

### Post by geertv on 2009-07-15
I was having a similar problem with a Tecra A10. 
Native resolution on the laptop : 1280x800
External display: HP LP2465 at 1920x1200

I would get the unable to pin front buffer whenever I tried forcing the external display over 1200x800.. 

What solved my problem was adding the "uxa-option" to the device section of xorg: 

[INDENT]Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"	"uxa"
EndSection[/INDENT]

Have a look at the following pages: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/304871]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/304871")
[https://wiki.ubuntu.com/X/UxaTesting]("https://wiki.ubuntu.com/X/UxaTesting")

Good luck ;-)

---

