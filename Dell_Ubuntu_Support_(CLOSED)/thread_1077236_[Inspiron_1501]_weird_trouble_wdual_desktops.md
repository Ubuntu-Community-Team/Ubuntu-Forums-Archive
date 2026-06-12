---
title: "[Inspiron 1501] weird trouble w/dual desktops"
date: 2009-02-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by alex_sv on 2009-02-22
Hi

I am new to ubuntu. Yesterday I've installed ubuntu 8.10 amd64 on my dell inspiron 1501 laptop. Almost all works fine except for dual desktop configuration.
I've noticed that I'm not alone with this particular problem, someone already faced this problem and even found solution for that (e.g. xorg.conf is given at [http://ubuntuforums.org/showthread.php?t=948703](http://ubuntuforums.org/showthread.php?t=948703))

But this did not help. Configuration via ATI Catalyst Control Center didn't help either.
The behavior of xserver becomes quite weird after applying any non-standard xorg.conf's. System just hangs after rebooting and monitor shows 3 different screens in an infinite loop: black, gray and 4-colored. Only manual power off can shut it down.

I tried to make it work all the night and now I've no idea what else I can try.

My secondary monitor is Samsung SyncMaster 960bg. Also I have latest proprietary ATI drivers installed.

My version of xorg.conf is as follows:

[FONT="Fixedsys"][SIZE="1"]
# xorg.conf (X.Org X Window System server configuration file)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"CorePointer"
	Option		"SHMConfig"
EndSection

Section "Device"
	Identifier	"Xpress 1150-1"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option		"XAANoOffscreenPixmaps" "true"
	Screen		0
EndSection

Section "Device"
	Identifier	"Xpress 1150-2"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option		"XAANoOffscreenPixmaps" "true"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Laptop Display"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"External LCD"
	Option		"DPMS"
	HorizSync	31.5 - 81.1
	VertRefresh	56 - 75
EndSection

Section "Screen"
	Identifier	"Primary Screen"
	Monitor		"Laptop Display"
	Device		"Xpress 1150-1"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Monitor		"External LCD"
	Device		"Xpress 1150-2"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "1024x768@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Primary Screen"
	Screen		"Secondary Screen" LeftOf "Primary Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"Generic Keyboard"
EndSection
[/SIZE][/FONT]

The output of lspci is as follows:
[FONT="Fixedsys"][SIZE="1"]
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
[/SIZE][/FONT]

The output of fxglrxinfo is as follows:
alex@udellalex:~$ fglrxinfo
display: :20.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.8087 Release


Help me, please !

---

### Post by alex_sv on 2009-02-23
Guys, is there any utility that automatically diagnoses all the monitor's modes - resolution+frequency, horizontal/vertical sync etc. in order to create **automatically** a configuration file (xorg.conf or whatever) use it and then analyze errors in case of bad monitor's performance?

One thing that drives me mad is that I need to reboot my computer each ******* time I introduce even smallest change in that xorg.conf file! I 
Ubuntu claims that it follow IJW = "It Just Works" principle, but is it so in case of tuning monitor's resolution??? I believe "It Just NOT Works" better suits my situation...
I recall "badly designed" Windows - it allow user to tune monitors resolution/frequency without any pain.

---

