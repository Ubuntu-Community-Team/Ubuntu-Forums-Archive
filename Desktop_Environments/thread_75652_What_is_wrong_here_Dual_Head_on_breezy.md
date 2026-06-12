---
title: "What is wrong here? Dual Head on breezy"
date: 2005-10-14
forum: Desktop Environments
---

### Post by jadacyrus on 2005-10-14
Okay, I've got a Nvidia GEForce 6800GT on AGP and an ATI Radeon 7200 on PCI. Both cards worked by themselves when I switched primary video device from PCI to AGP and so forth in the bios. However when I try to have both cards running a multi-screen display I get the following error:

> (WW) RADEON: No matching Device section for instance (BusID PCI:2:3:0) found
(--) Chipset ATI Radeon QD (AGP) found


However running an X :1 -scanpci shows that the device is there..

> root@nanofiber:/home/alex#  X :1 -scanpci
Probing for PCI devices (Bus:Device:Function)

(0:0:0) unknown card (0x8086/0x2570) using a Intel Corp. 82865G/PE/P Processor to I/O Controller
(0:1:0) Intel Corp. 82865G/PE/P Processor to AGP Controller
(0:29:0) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB USB
(0:29:1) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB USB
(0:29:2) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB USB
(0:29:3) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB USB
(0:29:7) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB USB2
(0:30:0) Intel Corp. 82801BA/CA/DB/EB PCI Bridge
(0:31:0) Intel Corp. 82801EB LPC Interface Controller
(0:31:1) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB Ultra ATA Storage Controller
(0:31:2) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB Ultra ATA Storage Controller
(0:31:3) unknown card (0x8086/0x524c) using a Intel Corp. 82801EB SMBus Controller
(0:31:5) unknown card (0x8086/0xe000) using a Intel Corp. 82801EB AC'97 Audio Controller
(1:0:0) unknown card (0x1043/0x81a3) using an unknown chip (DeviceId 0x0045) from nVidia Corporation
(2:1:0) unknown card (0x1102/0x0051) using a Creative Labs SB Audigy
(2:1:1) unknown card (0x1102/0x0040) using a Creative Labs SB Audigy MIDI/Game port
(2:1:2) unknown card (0x1102/0x0010) using a Creative Labs SB Audigy FireWire Port
(2:2:0) unknown card (0x1317/0x0570) using a Linksys Network Everywhere Fast Ethernet 10/100 model NC100
(2:3:0) unknown card (0x1002/0x0039) using a ATI Technologies Inc Radeon R100 QD [Radeon 7200]

This leads me to beleive it has somethign to do with my xorg.conf file, so here it is. is there something I am missing here? I've been trying to get this to work forever, this should be a simple thing.
Here is a snippet of the relevant stuff from /etc/X11/xorg.conf:
> 

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section	"Device"
	Identifier	"ATI Radeon 7200"
	Driver		"radeon"
	BusID		"PCI:2:3:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Generic Monitor 2"
	Option		"DPMS"
	HorizSYnc	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"NvidiaScreen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "ATIScreen"
        Device          "ATI Radeon 7200"
        Monitor         "Generic Monitor 2"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerFlags"
	Option	"Xinerama"	"ON"
EndSection

Section "ServerLayout"
	Identifier	"Dual Head Layout"
	Screen		0 "NvidiaScreen" 0 0
	Screen		1 "ATIScreen" LeftOf "NvidiaScreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


Please help me!

---

### Post by Ampersand on 2005-10-14
It's probably because you're using the nv and radeon drivers. Try following through the howto here:

[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

---

### Post by jadacyrus on 2005-10-15
You're right that makes sense... I'm going to try that.

---

### Post by jadacyrus on 2005-10-15
Okay, I got the correct nvidia driver (7147) installed and ive installed the fglrx driver for the ati card.. However the log file still complains about not having a match device section for PCI:2:3:0... The nvidia monitor loads up fine, the ATI monitor has a green LED but there is no picture at all... I tihnk i am getting closer..

---

### Post by carpy on 2005-10-27
I'll one-up you.
I'm running dual-head on a single ATI Radeon with two monitors.
This worked nearly from install of Hoary.
Installing Breezy (unfortunately, I lost my xorg.conf) on the same machine, and my second monitor shows up blank. (and the error message about the second card not being addressed also shows up for me too)

Here's the *real* kicker!  If I let the box sit and enter monitor powersave mode, when it comes back (ie. the monitors' amber lights turn to green), I'm in xinerama mode and everything works great until I restart X or log out.

email at [email]matt@eisgr.com[/email] if you find the solution.  Perhaps it will help me too.

thx!

---

