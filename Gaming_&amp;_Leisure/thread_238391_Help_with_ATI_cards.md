---
title: "Help with ATI cards"
date: 2006-08-17
forum: Gaming &amp; Leisure
---

### Post by ExMachina on 2006-08-17
Ok.. ive seen the Howtos .. ive done them all.. and i stil get mesa..

heres my xorg.conf. 
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
```

thats the original.
Ive change "ati" to  "fglrx" and then X wont run.

I wanna play quake4 so bad. Anyone know how to help? Ill give oyu any info you need.

---

### Post by edemark on 2006-08-17
Hi 

I do not know if it will help you but may be. 
I have a hp compaq nx9010 

this is my lspci -V
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0300000-c03fffff
        Prefetchable memory behind bridge: d0000000-dfffffff

and this are the relevant part of my xorg.conf:
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IG$        Driver          "ati"
        BusID           "PCI:1:5:0"
EndSection

which is similar to yours. However i have this at the end of my xorg.conf:

Section "DRI"
        Mode    0666
EndSection

Ok so as far as I know you wont be able to use fglrx drives and have to stick to the open ati driver that comes with xorg this is somehow just a half way driver as you do have 3D acceleration but somehow slow also you have direct rendering. I am not sure if you can make quake4 to work but there might be some chance as half of the games that i try because i know that it works on linux actually work on my ati card. 

good luck

---

### Post by ExMachina on 2006-08-17
i have that

Section "DRI"
Mode 0666
EndSection

too..

what modeuls should be on and what SHOUDL i dl?
ALL games lag.

---

### Post by ExMachina on 2006-08-18
Mind postign you xorg.conf?

Maybe im configureing mine wrong..

I do EVEYRHTIGN it says and i egt the " no screen found " error

---

### Post by edemark on 2006-08-18
Hi so I can not offer to much for you as I am actually in the same issue of making my ati igp 345 work well. I have many issues which for I just cannot find answers so far. 
I know that the card has direct rendering as well as it can work in opengl mode, however none of these works perfect. For instance i wanted to play freespace 2 on this card. The funny staff is that icculus.org installer makes it work but the cvs checkout version from hard-light.net would only work in software rendering mode and not in opengl one. 
On the other side for instance cedega is even more tricky:
though you have it does not gets your 3D acceleration. As you can observe in the first picture actually it runs the three gears of glxgears. However as you can observe in the second attachment it fails this exact test. And here comes the fun part of my card it i do not le the gears to stay in the fromt (lets say i grab the test result window and move it that actually causes the gears to drop behind the main cedega window that the test is passed as you may observe on the 3rd attachment.

my xorg.conf is this: 


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
	Load	"i2c"
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
	Option		"XkbLayout"	"latam"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


I actually do not know what to expect I really would like some geek to see this message and to help us as you might have allready realized that i am just an eternal newbeee user who is not ment to resolve a problem like this

but good luck.

pd some games that work ok on my hp nx9010 Pharaon Ceasar III Emperor Black and White (basically older games) I have also tried quake 3 Arena in cedega and it worked well and of course the mayority of linux games like pp racer tremulus torcs trigger etc.

---

### Post by jackkerouac on 2006-08-18
Did you try blacklisting agpgart? I couldn't get fglrx working on my ATI with ANY howto until I did that. 

Now it works great.

---

### Post by ExMachina on 2006-08-18
How do i do that?

I ran though 3 tutorials.. if oyu need my fglxinfo , or my xorg ill post both

---

### Post by edemark on 2006-08-19
Dear Jackkerouac 

Could you be a bit more specific? What ati card you have? (do you have an ati igp 345 like me and you could make it work with fglrx driver)
Could you indicate which driver you used and how.
can we get some xorg.conf and for instance lspci -v and other stuff like that?


pls help

thanks

---

### Post by jackkerouac on 2006-08-19
Sorry, sure.

lspci -v

```

0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 2302
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 217
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at d800 [size=256]
        Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at feac0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] Secondary
        Subsystem: ATI Technologies Inc: Unknown device 2303
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at feae0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

```

Xorg.conf

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

# Section "Device"
#	Identifier  "ATI Technologies, Inc. Radeon X700 Pro (RV410)"
#	Driver      "ati"
#	BusID       "PCI:1:0:0"
# EndSection

# Section "Device"
#	Identifier  "aticonfig-Device[0]"
#	Driver      "fglrx"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
# EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option 	    "UseInternalAGPGART" "no"
	Option	    "RenderAccel" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID	    "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "aticonfig-Device[0]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

And I'm running an ATI X700.

Nothing, and I mean NOTHING worked for me until I did the following:

```

sudo gedit /etc/modprobe.d/blacklist

```

and then added

```

# blacklist agp stuff
blacklist agpgart
blacklist sis-agp

```

and then used [this tutorial]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually").

---

### Post by edemark on 2006-08-19
Hi and thanks for the quick reply

As I observe you have an ati x700 pro. On the other hand I have an integrated graphics chip called radeon igp 345. Thus I am not convinved that the fglrx driver supports this card. 
Thanks anyway I might try it out even though I am afraid that it would not work rhat make me doubt if it worth trying.

thanks again

---

### Post by ExMachina on 2006-08-19
FOund out some sad info form [http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html]("http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html")

Radeon is a Xorg driver for ATI RADEON based video cards. It contains full support for 8, 15, 16 and 24 bit pixel depths, dual-head setup, flat panel, hardware **2D acceleration, hardware 3D acceleration (except R300 and IGP series cards**), hardware cursor, XV extension, Xinerama extension.

[b]RS200
    Radeon IGP330(M)/IGP340(M) (2D only)[/b]

Thats my card >.<
I HATE YOU ATI 2 week of thi stuff and I cant play flippin games on my laptop now

---

### Post by edemark on 2006-08-21
Hi back again 

first you may clearly express you anger, writing to ati asking them to releasy decente linux driver.
On the second place I have found something that might help.
the issue is changing from ati to radeon driver.

According to this page [http://ftp.x.org/pub/X11R6.9.0/doc/html/radeon.4.html](http://ftp.x.org/pub/X11R6.9.0/doc/html/radeon.4.html)
igp 330 and igp 340 has 3D support.
You might also have a look on this:
[http://ubuntuforums.org/archive/index.php/t-11365.html](http://ubuntuforums.org/archive/index.php/t-11365.html)

good luck

---

### Post by edemark on 2006-08-21
just in case you are still interested i have started a thread in the hardware forum trying to find answers:

[http://www.ubuntuforums.org/showthread.php?t=241092](http://www.ubuntuforums.org/showthread.php?t=241092)

bye

---

### Post by edemark on 2006-08-25
Just one thing that made me happy

[http://www.ubuntuforums.org/showthread.php?t=221672](http://www.ubuntuforums.org/showthread.php?t=221672)
The suggested in this htread works on my:
"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"

before I got some 300 fps in glxgears now I have 1100 
It works

good luck
and now i pass cedega test

---

