---
title: "Starcraft slow under Ubuntu; fine under Slackware?"
date: 2004-12-05
forum: Gaming &amp; Leisure
---

### Post by Neo40 on 2004-12-05
Hi,

I really like Ubuntu. My system is perfect so far! Today, I installed starcraft (and broodwar) with cedega. The cinematic is playing fine but when I play a game it is a bit slow when I compare it with Slackware 10.  Yes, I have Nvidia driver installed. Is it just me with this problem? Any suggestions?

Thanks in advance!

EDIT: Nevermind. I rebooted my machine and SC is playing just great!

---

### Post by patrick295767 on 2006-06-03
I have it running without any problem.
I played today with it !! 
Long time I didnt, was great game ! Protoss are very nice to be played with Broodwar. 
  
I have an ATI and I am sure with the nvidia, it can work. Could you post your /etc/X11/xorg.conf ?

Greetz

---

### Post by Micoz on 2006-07-08
I have similar problem. I istalled cedega 5.1 today and installed using it Starcraft. Ok, it started, logos showed, and... The menu and the rest of the game is SLOOOW. I don`t know how to make it faster. Could you help me?

I use Ubuntu Dapper Drake.

my /etc/X11/xorg.conf
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
   	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"FLATRON L151"
	Option		"DPMS"
	HorizSync	31-61
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"FLATRON L151"
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
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by ed_agamemnon on 2006-07-08
start the game with:

```
nice -n 20 wine "/wherever/starcraft.exe"
```

---

### Post by Micoz on 2006-07-10
Ok, but how to force it to use CD-ROM? I can`t run it, cuz` it doesn`t see cd in drive.

---

### Post by Neo40 on 2006-07-13
Open up Cedega, right click on the icon Starcraft and select edit profile. On general tab, make sure scheduler is set to "No". It should work now!

---

