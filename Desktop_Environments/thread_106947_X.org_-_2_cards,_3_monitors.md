---
title: "X.org - 2 cards, 3 monitors?"
date: 2005-12-21
forum: Desktop Environments
---

### Post by propadog on 2005-12-21
Hi,

I'm currently running a two monitor setup using X.org. The video card is an nVidia Quadro 4 200/400 NVS, using the "nvidia" driver. The second monitor is listed as an option in the video card "Device" section and works perfectly.

What I'm looking at doing is adding a second nVidia card, an MX200 single output, and running over three monitors.

Everything seems fine with two video card devices in xorg.conf, but it is barfing at the monitor section. It seems to expect only one listing, so if I try an additional one, it spits me out on start.

Any ideas how I get the third monitor recognised?

---

### Post by lisje on 2005-12-22
I think you already found that you need xinerama... could you give us your xorg.conf?

---

### Post by mo_x on 2005-12-22
Post your /etc/X11/xorg.conf and /var/log/Xorg.0.log as attachments.
Also what monitors are you using and how are they connected to the video cards.
Also post the output of the command lspci.

---

### Post by propadog on 2005-12-23
lspci:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:04.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:09.0 Ethernet controller: Intel Corp. 82540EM Gigabit Ethernet Controller (rev 02)
0000:00:0b.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:0b.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:0b.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:0b.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0000:00:0c.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
0000:00:0d.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17GL [Quadro4 200/400 NVS] (rev a3)


xorg.conf

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "ServerFlags"
	
EndSection


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17GL [Quadro4 200/400 NVS]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		0
	Option 		"NvAGP" "2"
	Option 		"NoLogo" "0"
	Option 		"RenderAccel" "0"
	Option 		"CursorShadow" "1"
	Option 		"Coolbits" "1"
	Option 		"ConnectedMonitor" "crt, crt"
	Option 		"NoPowerConnectorCheck"
	Option 		"TwinView" "1"
	Option 		"Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1024x768,NULL"
	Option 		"SecondMonitorHorizSync" "31-82"
	Option 		"SecondMonitorVertRefresh" "56-76"
# 	Option 		"NoTwinViewXineramaInfo"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Driver		"nvidia"
	BusID		"PCI:0:12:0"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor2"
	Option		"DPMS"
EndSection

Section "Screen"
	Device		"NVIDIA Corporation NV17GL [Quadro4 200/400 NVS]"
	Identifier 	"Default Screen"
	Monitor 	"Monitor0"
	DefaultDepth 	24
	SubSection "Display"
		Depth		1
		Viewport 	0 0
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Viewport 	0 0
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Viewport 	0 0
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Viewport 	0 0
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Viewport 	0 0
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Viewport 	0 0
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Monitor		"Monitor2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
Identifier  "Default Layout"
    	Screen      	0 "Screen0"
    	Screen      	2 "Screen2" leftOf "Screen0"
	InputDevice 	"Configured Mouse"
	InputDevice 	"Generic Keyboard"
	Option 		"Xinerama" "On"
EndSection


Can't provide the xorg log file - but it says that it can't find screens.

Cheers.

---

### Post by mo_x on 2005-12-24
You refer to "Screen0" in the ServerLayout but there is no such identifier.
I have attached an xorg.conf you can try. It is not using TwinView but 3 seperate X screens. I am not able to test it so there might some typo's in it :)
If it is not working than please post xorg.conf and /var/log/Xorg.0.log (as attachments).

---

### Post by propadog on 2005-12-29
[QUOTE=mo_x]You refer to "Screen0" in the ServerLayout but there is no such identifier.
I have attached an xorg.conf you can try. It is not using TwinView but 3 seperate X screens. I am not able to test it so there might some typo's in it :)
If it is not working than please post xorg.conf and /var/log/Xorg.0.log (as attachments).[/QUOTE]

Hi, folks.  No luck with this one yet.


From line 78, the Xorg log file says:

(II) PCI: 00:0c:0: chip 10de,0111 card 0000,0000 rev b2 class 03,00,00 hdr 00

At line line 282:

(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:12:0) found

lspci says:

0000:00:0c.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)

so to me that all seems correct.

The additional video card works as a single card. I pulled the AGP card and ran dpkg-reconfigure xserver-xorg, and that all corresponds with what is in the new xorg.conf file. So I've eliminated a dud card.

I'm probably barking up the wrong tree, but any help would be appreciated.

Attached are:

xorg log file
xorg.conf files used to generate this error;
lspci dump

---

### Post by mo_x on 2006-01-03
Hello propadog,

Please remove the "Screen 2" line from the device section of the Geforce2 card in your xorg.conf and try again.
If that doesn't help I am affraid I don't have an answer. You can try posting your problem on the nvidia linux forum.
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

mo_x

---

