---
title: "TwinView w/ 2 cards?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Ne0MindlesS on 2006-06-08
I have been running Ubuntu for a couple weeks now but still have not been able to enable my second monitor =( I see the guides/How To's posted for dualies in Ubuntu are just about all written for a 1 card / 2 connections type setup.  I however, have 2 seperate video cards 1) Nvidia GeForce2 (which i currently use) and a s3 ViRGE connected to another monitor that is not enabled...I see ViRGE Dx/ or /GX in the device manager, but other than that i dont have a clue..any one know how to get this working?

---

### Post by murataht on 2006-06-08
thats a interesting task. you have to mess up with your xorg.conf file. did you do someting already in it? can you post it here? maybe people here can give you some hints according to your xorg.conf file.

---

### Post by denjin on 2006-06-08
[LEFT]I think you need to use xinerama if both aren't nvidia, don't you?

I use xinerama with a 5700LE and an onboad 915G just fine.  Post us your xorg.conf file. :)

Here is an example of how mine is setup (for 3 displays):
```


Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option      "AllowGLXWithComposite" "true"
        Option "DRI" "true"
EndSection

Section "Device"
        Identifier      "5700LE-0"
        Driver          "nvidia"
        BusID           "PCI:5:9:0"
        screen 0
        Option      "AllowGLXWithComposite" "true"
        Option  "RenderAccel"   "true"
EndSection

Section "Device"
        Identifier      "5700LE-1"
        Driver          "nvidia"
        BusID           "PCI:5:9:0"
        screen 1
        Option      "AllowGLXWithComposite" "true"
        Option  "RenderAccel"   "true"
EndSection


Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "Default Screen" 0 0
        Screen          "Screen 0" RightOf "Default Screen"
        Screen          "Screen 1" LeftOf "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "Xinerama"      "on"
EndSection


``` 
Just an example...not my whole xorg.conf.  You'll need the monitor parts in it, etc.  But the parts above are very important.  The lspci command should help you figure out the BusID of your cards.  Here is what my lspci says for my two cards so you can see how to convert it to the info above:
```

0000:00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04)
0000:05:09.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)

```
[/LEFT]

---

### Post by Ne0MindlesS on 2006-06-08
here is my xorg.conf:


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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL M782"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"DELL M782"
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




i've never modified it before i dont believe...so remember your talking to a n00b lol

---

### Post by denjin on 2006-06-09
Ok, to help you out more, we need the output from 'lspci'. :)  

Basically, we need to get you setup with two Device sections (one for each video card), and then possible two Monitor and Screen sections.  Then, edit the ServerLayout portion after we get that done.

---

### Post by Ne0MindlesS on 2006-06-12
[QUOTE=denjin]Ok, to help you out more, we need the output from 'lspci'. :)  

Basically, we need to get you setup with two Device sections (one for each video card), and then possible two Monitor and Screen sections.  Then, edit the ServerLayout portion after we get that done.[/QUOTE]


chris@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host B ridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bri dge (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Au dio (rev 05)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
0000:02:09.0 VGA compatible controller: S3 Inc. ViRGE/DX or /GX (rev 01)
0000:02:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip co mpatible 10/100 Ethernet (rev 31)
chris@ubuntu:~$



p.s. when I'm trying to post something like this that includes code, how do i put it in one of those fancy code boxes that i've seen used everywhere ?(similar to quote boxes)

---

