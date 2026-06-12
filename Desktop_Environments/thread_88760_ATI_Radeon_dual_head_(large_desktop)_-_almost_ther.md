---
title: "ATI Radeon dual head (large desktop) - almost there"
date: 2005-11-11
forum: Desktop Environments
---

### Post by JakeSpeare on 2005-11-11
OK, I finally decided to give 3d acceleration a go.  I have been using the generic ati drivers and have had a fantastic large desktop where I can drag and drop and do as I please.  It is a bit sluggish at times though.

My xorg.conf that works for that scenario is this:

> ection "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Identifier	"videocard0"
	Driver		"ati"
EndSection

Section "Device"
	Identifier	"videocard1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync 31.0 - 80.0
	VertRefresh 55.0 - 75.0
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
	HorizSync 31.0 - 80.0
	VertRefresh 55.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device "videocard1"
	Monitor "Monitor1"
	DefaultDepth 24
	Subsection "Display"
		Viewport 0 0
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection

Section "ServerLayout"
	Identifier	"Multihead Layout"
	Screen		0 "Screen0" RightOf "Screen1"
	Screen		1 "Screen1" 0 0 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option "Xinerama" "on"
	Option "Clone" "off"
EndSection


I have edited this file to get the fglrx drivers going and I get two identical desktops with this xorg.conf (I get fantastic fps and it is fast).  I can, however, for the life of me, not get a large desktop!:

> Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"GLcore"
	#Load	"extmod"
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Identifier	"videocard0"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		0

# === Video Overlay for the Xv extension ===
  	Option 		"VideoOverlay" 		"on"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  	Option 		"OpenGLOverlay" 	"off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  	Option 		"UseInternalAGPGART" 	"no"


EndSection

Section "Device"
	Identifier	"videocard1"
	Driver		"fglrx"
#	BusID		"PCI:1:0:1"
	Screen 		1

# === Video Overlay for the Xv extension ===
  	Option 		"VideoOverlay" 		"on"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  	Option 		"OpenGLOverlay" 	"off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  	Option 		"UseInternalAGPGART" 	"no"

EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync 31.0 - 80.0
	VertRefresh 55.0 - 75.0
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
	HorizSync 31.0 - 80.0
	VertRefresh 55.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
	EndSubSection
EndSection

Section "Screen"
	Identifier 	"Screen1"
	Device 		"videocard1"
	Monitor 	"Monitor1"
#	Viewport 0 0
	DefaultDepth 	24
	Subsection "Display"
		Depth 		24
		Modes 		"1280x1024"
	EndSubSection
EndSection

Section "DRI"
#	Group 0
	Mode 0666
EndSection

Section "ServerLayout"
	Identifier	"Multihead Layout"
	Screen	0 	"Screen0" RightOf "Screen1"
	Screen	1 	"Screen1" 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option 		"Xinerama" "on"
	Option 		"Clone" "off"
EndSection



I have commented out and tried stuff back and forth for hours to no avail!

What am I missing?  

Thanks for any and all help and tips!

:confused:

---

### Post by Morrigu on 2005-11-11
What fglrx version are you using?

---

### Post by JakeSpeare on 2005-11-11
[QUOTE=Morrigu]What fglrx version are you using?[/QUOTE]

when I run fglrxinfo i get:

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)


I have an identical desktop on both displays.

my current xorg.conf is:

> Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"GLcore"
	#Load	"extmod"
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Identifier	"videocard0"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		0

# === Video Overlay for the Xv extension ===
  	Option 		"VideoOverlay" 		"on"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  	Option 		"OpenGLOverlay" 	"off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  	Option 		"UseInternalAGPGART" 	"no"


EndSection

Section "Device"
	Identifier	"videocard1"
	Driver		"fglrx"
#	BusID		"PCI:1:0:1"
	Screen 		1

# === Video Overlay for the Xv extension ===
  	Option 		"VideoOverlay" 		"on"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  	Option 		"OpenGLOverlay" 	"off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  	Option 		"UseInternalAGPGART" 	"no"

EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync 31.0 - 80.0
	VertRefresh 55.0 - 75.0
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
	HorizSync 31.0 - 80.0
	VertRefresh 55.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
	EndSubSection
EndSection

Section "Screen"
	Identifier 	"Screen1"
	Device 		"videocard1"
	Monitor 	"Monitor1"
#	Viewport 0 0
	DefaultDepth 	24
	Subsection "Display"
		Depth 		24
		Modes 		"1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection

Section "ServerLayout"
	Identifier	"Multihead Layout"
	Screen	0 	"Screen0" RightOf "Screen1"
	Screen	1 	"Screen1" 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	Option 		"Xinerama" "on"
#	Option 		"Clone" "off"
EndSection


---

### Post by dro0g on 2005-11-11
I've had the same problem with a Dell D600 laptop. I have the fglrx driver working with the laptop screen, but when I try to use it with the two video ports (one analog, one DVI) on my docking station it locks the screen. I can get fglrx working in sort of mirrored mode (the image on the analog connected screen is misaligned)

I have a working xorg.conf for the dual screens using the radeon driver that works ok (though I had to do some crazy weird stuff to get it to display on the analog connected screen)

---

### Post by JakeSpeare on 2005-11-11
[QUOTE=dro0g]
I have a working xorg.conf for the dual screens using the radeon driver that works ok (though I had to do some crazy weird stuff to get it to display on the analog connected screen)[/QUOTE]

Can you post it here?

---

### Post by JakeSpeare on 2005-11-14
<<bump>>

in hope of help from someone.

:)

---

### Post by JakeSpeare on 2005-11-15
YES!!!!

After much reading and trying I got the fR#$!#%!@%!$%^!@#$%n thing working!

I've got great framerates and my interface is MUCH snappier! 

I am very happy now.

Here is my xorg.conf for anyone who is interested:

> Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "ServerFlags"
#	Option		"Xinerama" "on"
#	Option 		"Clone" "off"
#	Option		"MergedFB" "on"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
#	Load	"GLcore"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Identifier	"videocard0"
#	Driver		"ati"
	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	Option		"UseInternalAGPGART"	"no"
	Option		"no_accel" 		"no"
	Option		"no_dri"		"no"
	Option		"mtrr"			"off"
    	Option 		"DesktopSetup"          "Horizontal"
	Option		"MonitorLayout"		"AUTO, AUTO"
	Option		"MetaModes"		"1280x1024-1280x1024"
	Option		"IgnoreEDID"		"off"
	Option		"NoTV"			"no"
	BusID		"PCI:1:0:0"
	Screen		0

EndSection

Section "Device"
	Identifier	"videocard1"
	Driver		"fglrx"
	BusID		"PCI:1:0:1"
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync 31.0 - 80.0
	VertRefresh 55.0 - 75.0
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
	HorizSync 31.0 - 80.0
	VertRefresh 55.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device "videocard1"
	Monitor "Monitor1"
	DefaultDepth 24
	Subsection "Display"
#		Viewport 0 0
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "DRI"
#	Group 0
	Mode 0666
EndSection

Section "ServerLayout"
	Identifier	"Multihead Layout"
	Screen		0 "Screen0" RightOf "Screen1"
#	Screen		1 "Screen1" 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	Option "Xinerama" "on"
#	Option "Clone" "off"
EndSection

---

### Post by nianhbg on 2005-11-16
Thanks it works for me too :)

---

### Post by Kingedgar on 2006-02-06
HI this works great on my d600, with a M9 chip. My only problem is the monitor sits to the left of the laptop screen, while it acts like it sits to the right.

I have played with different RightOf, even a LeftOf out of the following section

> Section "ServerLayout"
Identifier "Multihead Layout"
Screen 0 "Screen0" RightOf "Screen1"
# Screen 1 "Screen1"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
# Option "Xinerama" "on"
# Option "Clone" "off"
EndSection

Could someone direct me to the correct syntax for extending the desktop to the left, instead of the right... 

I still want icons and taskbars centerd in my main laptop screen, just want to be able to drag stuff to the left instead of the right.

Thanks,

Jason

---

### Post by FrankTM on 2006-02-06
i got it working, almost

I have two screen connected and working at 1600x1200 now.
Had to put both devices on **BusID "PCI:1:0:0"** to get this to work.


the only thing is, i can't drag stuff from one monitor to the other
any suggestions to make that work?

i have attached my xorg.conf

the config also complained that there was no Screen1
had to enable it in the ServerLayout, doing:
```
	Screen 0 "Screen0" RightOf "Screen1"
	Screen 1 "Screen1
```

---

### Post by dro0g on 2006-02-10
Here's my config for anyone still interested. This is on a Dell D600. I have two xorg.conf files - one for when I'm using the built-in screen, and one for when I'm at work where I use two Dell 1905FP LCDs. There's still some cruft in there from when I was playing around trying to get things working. You'll notice in the docked config that I have to do some weird stuff with the frequency, etc. to get the two LCDs to display correctly since one is using the analog port and one on DVI.

This is not an ideal solution but it works. I have to run sudo profile.sh and pick the whether I'm docked or not and then restart X.

[ATTACH]6018[/ATTACH]

[ATTACH]6019[/ATTACH]

[ATTACH]6020[/ATTACH]

---

### Post by FrankTM on 2006-02-10
[QUOTE=dro0g]Here's my config for anyone still interested. This is on a Dell D600. I have two xorg.conf files - one for when I'm using the built-in screen, and one for when I'm at work where I use two Dell 1905FP LCDs. There's still some cruft in there from when I was playing around trying to get things working. You'll notice in the docked config that I have to do some weird stuff with the frequency, etc. to get the two LCDs to display correctly since one is using the analog port and one on DVI.

This is not an ideal solution but it works. I have to run sudo profile.sh and pick the whether I'm docked or not and then restart X.

[ATTACH]6018[/ATTACH]

[ATTACH]6019[/ATTACH]

[ATTACH]6020[/ATTACH][/QUOTE]
you are not using the fglrx driver

and can u drag an application from one screen to the other?

---

### Post by dro0g on 2006-02-10
[QUOTE=FrankTM]you are not using the fglrx driver
[/QUOTE]

The single screen config uses fglrx. I have not been able to get the fglrx driver to work with the dual config.

[QUOTE=FrankTM]
and can u drag an application from one screen to the other?[/QUOTE]

Yes, it's one big desktop. You can drag apps around to your hearts content.

---

### Post by FrankTM on 2006-02-10
[QUOTE=dro0g]The single screen config uses fglrx. I have not been able to get the fglrx driver to work with the dual config.
[/QUOTE]

look back in this thread somewhat, and try to play around with my xorg.conf a bit... that's a dual-screen setup with fglrx
you'll probably need to adjust the monitor settings, but I guess you can copy/paste a bit from your own setup :P

[QUOTE=dro0g]
Yes, it's one big desktop. You can drag apps around to your hearts content.[/QUOTE]

I like the dual screen as Windows implemented it
like the default xorg, with two seperate screens, but with the ability to drag programs from one screen to another
I go bananas if I use xinerama :P

---

### Post by copilot on 2006-02-17
Endless thanks for the guide, I'm dragging windows all over the place now. I'm kind of unhappy with trying to watch fullscreen vids though. anyone know of a way I can watch vids full screen on one and still use the other?

---

