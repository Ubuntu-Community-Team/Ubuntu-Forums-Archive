---
title: "feisty fawn + beryl + nvidia + dual monitors"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by ZypherXII on 2007-08-21
Hey all,
I was randomly browsing around youtube when i came across some videos featuring ubuntu using two monitors and beryl.

This is one of them:
[http://youtube.com/watch?v=DRwEVef1ywU]("http://youtube.com/watch?v=DRwEVef1ywU")

I also noticed in some if the videos they use twinview and others they use separate desktops with to independent cubes spinning around.

Does anybody know how to setup this kind of stuff? I've spend hours of googling around without any luck.

I just installed a clean version of ubuntu, updated and donwloaded nvidia-glx. And I setup twinview perfectly, but when using beryl it simply ignores my second desktop. 

This is my specs:
Pentium D 3,6 ghz
2gb DDRII dual-channel
XFX GeForce 7900GS

I appreciate any help and/or links to guides.

Thanks in advance.

--
Cheers,
ZypherXII

---

### Post by overdrank on 2007-08-22
HI and maybe this will help
[http://www.tldp.org/HOWTO/Xinerama-HOWTO/](http://www.tldp.org/HOWTO/Xinerama-HOWTO/)
[http://ubuntuforums.org/showthread.php?t=361124](http://ubuntuforums.org/showthread.php?t=361124)
Good luck!

---

### Post by hfw on 2007-08-22
Is it spinning one giant cube, or is it spinning a single small cube for one monitor, and not rotating the other monitor?

I use twinview as well on a two monitor set up, and by default it rotated my desktop as one giant cube.

There is a setting somewhere in Beryl Manager that will set it as two seperate cubes.  I am not sure where though, and am at work on my Windows machine.

Good Luck,
hal

---

### Post by ZypherXII on 2007-08-24
Okay, thanks for the replies both of you. Let's wrap things up:

I have a ubuntu system with one nVidia videocard. I've hooked up two LCD thorugh DVI to it. I am trying to get to seperate desktop with two separate cubes. I've until now managed to setup separate x screens with the helt of the links that you guys posted.

This is what my xorg.conf looks like:
[HTML]
Section "ServerLayout"
	Identifier	"Layout"
	InputDevice	"Keyboard"	"CoreKeyboard"
	InputDevice	"Mouse"		"CorePointer"	
	Screen		0		"Screen0"		0		0
	Screen		1		"Screen1"		RightOf		"Screen0"
	Option		"AIGLX"		"true"
	Option		"Xinerama"	"false"
EndSection

Section "Module"
	Load		"dri"
	Load		"glx"
	Load		"vbe"
	Load		"dbe"
	Load		"extmod"
	Load		"freetype"
	Load		"type1"
	Load		"GLcore"
EndSection

Section "Files"
	RgbPath		"/usr/X11R6/lib/X11/rgb"
EndSection


Section "InputDevice"
	Identifier	"Keyboard"
	Driver		"kbd"
	Option		"XkbModel"		"logiik"
	Option		"XkbLayout"		"dk"
EndSection

Section "InputDevice"
	Identifier	"Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto"
	Option		"Emulate3Buttons" 	"no"
	Option		"Buttons"		"5"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	VendorName	"NVIDIA Corporation"
	BoardName	"GeForce 7900 GS"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"NoLogo"		"false"
	Option		"RenderAccel"		"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"SecondMonitorHorizSync" "31.0 - 81.0"
	Option		"SecondMonitorVertRefresh" "56.0 - 76.0"
EndSection

Section "Device"
	Identifier	"Videocard1"
	Driver		"nvidia"
	VendorName	"NVIDIA Corporation"
	BoardName	"GeForce 7900 GS"
	BusID		"PCI:1:0:0"
	Screen		1
	Option		"NoLogo"		"false"
	Option		"RenderAccel"		"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"SecondMonitorHorizSync" "31.0 - 81.0"
	Option		"SecondMonitorVertRefresh" "56.0 - 76.0"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"Xerox"
	ModelName	"XER XA7-17i"
	HorizSync       31.0 - 81.0
    	VertRefresh     56.0 - 76.0
	Option		"DPMS"
EndSection

Section	"Monitor"
	Identifier	"Monitor1"
	VendorName	"Xerox"
	ModelName	"XL775"
	HorizSync       31.0 - 81.0
    	VertRefresh     56.0 - 76.0
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Monitor0"
	Device		"Videocard0"
	DefaultDepth	24
	
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"	"1024x768"	"800x600"
	EndSubSection

	SubSection "Display"
		Depth		23
		Modes		"1024x768"	"800x600"
	EndSubSection

	SubSection "Display"
		Depth		22
		Modes		"800x600"
	EndSubSection

	Option         "metamodes" "dfp-0: 1280x1024 +0+0; dfp-0: 1024x768 +0+0; dfp-0: 800x600 +0+0; dfp-0: 640x480 +0+0"
EndSection

Section "Screen"
	Identifier	"Screen1"
	Monitor		"Monitor1"
	Device		"Videocard1"
	DefaultDepth	24
	
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"	"1024x768"	"800x600"
	EndSubSection

	SubSection "Display"
		Depth		23
		Modes		"1024x768"	"800x600"
	EndSubSection

	SubSection "Display"
		Depth		22
		Modes		"800x600"
	EndSubSection

	Option         "metamodes" "dfp-0: 1280x1024 +0+0; dfp-0: 1024x768 +0+0; dfp-0: 800x600 +0+0; dfp		-0: 640x480 +0+0"
EndSection

Section "DRI"
	Mode		0666
Endsection

Section "Extensions"
	Option		"Composite"		"Enable"
EndSection
[/HTML]

Now everything is working fine except some few things.. When I rightclick on the desktop or if i try open the apllications/places/system menus on my left (main) screen, takes about 2-3 seconds before it shows up. My avant-window-navigator is hiding the icons behind the dock itself. And on my right (second) screen the window decorator does not work.

Any suggestions?

And thanks again...

---

### Post by ZypherXII on 2007-08-25
Okay, I finally gave up on running the screens as separate X Screens and I'm now using Twinview and everything is running perfectly and I'm also having to separate cubes spinning.

To others who might be curious my xorg.conf looks like this now:

[HTML]
Section "ServerLayout"
	Identifier	"Layout"
	InputDevice	"Keyboard"	"CoreKeyboard"
	InputDevice	"Mouse"		"CorePointer"		
	Option		"AIGLX"		"true"
	Option		"Xinerama"	"0"
	Screen		0		"Screen0"	0	0
EndSection

Section "Module"
	Load		"dri"
	Load		"glx"
	Load		"vbe"
	Load		"dbe"
	Load		"ddc"
	Load		"bitmap"
	Load		"extmod"
	Load		"freetype"
	Load		"type1"
	Load		"int10"
	Load		"GLcore"
EndSection

Section "Files"
	RgbPath		"/usr/X11R6/lib/X11/rgb"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "InputDevice"
	Identifier	"Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbModel"		"logiik"
	Option		"XkbLayout"		"dk"
EndSection

Section "InputDevice"
	Identifier	"Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto"
	Option		"Emulate3Buttons" 	"yes"
	Option		"Buttons"		"5"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	VendorName	"NVIDIA Corporation"
	BoardName	"GeForce 7900 GS"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"NoLogo"		"false"
	Option		"RenderAccel"		"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"SecondMonitorHorizSync" "31.0 - 81.0"
	Option		"SecondMonitorVertRefresh" "56.0 - 76.0"
	Option		"metamodes" "dfp-0: 1280x1024 +0+0, dfp-1: nvidia-auto-select +1280+0; dfp-0: 1024x768 +0+0, dfp-1: nvidia-auto-select +1024+0; dfp-0: 800x600 +0+0, dfp-1: nvidia-auto-select +800+0; dfp-0: 640x480 +0+0, dfp-1: nvidia-auto-select +640+0"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"Xerox"
	ModelName	"XER XA7-17i"
	HorizSync       31.0 - 81.0
    	VertRefresh     56.0 - 76.0
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Monitor0"
	Device		"Videocard0"
	Option		"TwinView"		"1"
	DefaultDepth	24
	
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"	"1024x768"	"800x600"
	EndSubSection

	SubSection "Display"
		Depth		23
		Modes		"1024x768"	"800x600"
	EndSubSection

	SubSection "Display"
		Depth		22
		Modes		"800x600"
	EndSubSection

	Option         "metamodes" "dfp-0: 1280x1024 +0+0, dfp-1: nvidia-auto-select +1280+0; dfp-0: 1024x768 +0+0, dfp-1: nvidia-auto-select +1024+0; dfp-0: 800x600 +0+0, dfp-1: nvidia-auto-select +800+0; dfp-0: 640x480 +0+0, dfp-1: nvidia-auto-select +640+0"
EndSection

Section "Extensions"
	Option		"Composite"		"Enable"
EndSection

Section "DRI"
	Mode		0666
Endsection
[/HTML]

Thanks for the help ;)

~Thread Closed~

---

