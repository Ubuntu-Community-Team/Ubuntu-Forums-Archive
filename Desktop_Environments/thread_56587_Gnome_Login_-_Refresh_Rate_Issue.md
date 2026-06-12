---
title: "Gnome Login - Refresh Rate Issue"
date: 2005-08-13
forum: Desktop Environments
---

### Post by duminas on 2005-08-13
[size=1](Illdian, at least I didn't ask this immediately in that other thread. :P)[/size]

Question number two.
My login screen with GNOME is acting weird. I've got a solid white line going down the right side of the display (it's like this is just really, really bright), and that area of the screen, however small, is impossible to view. Additionally, the screen acts kind of funky--shakes, almost.

In my searching, I found [this](http://ubuntuforums.org/showthread.php?p=253944&highlight=login+screen+refresh+rate#post253944) which sounds similar to my problem. However, I can not get that to work on mine.

I want to get the login screen to go at 60 Hz, instead of the 70+ it is right now.
I'm using the 'nv' driver; the default Ubuntu stuck on here.

I know I got these values from somewhere, but I cannot recall where (they are for my monitor):
```
        HorizSync       30-58
        VertRefresh     50-120
```Thought they might be pertinent.
If I need to post my xorg.conf, by all means, ask.

Thanks for any help, again, guys~

---

### Post by Lord Illidan on 2005-08-13
Hi Duminas, nice helping you again!

It would be helpful if you posted your xorg.conf..

Also, some of your specs... 

What graphics card do you have? If you have an NVIDIA card, and I think you do, you can install the official nvidia drivers from Synaptic, just follow the ubuntu guide : [www.ubuntuguide.org](http://www.ubuntuguide.org) 

What monitor do you have, a TFT or a CRT?

Also, you might want to edit your xorg.conf and change the nv to 'vesa', at least until you get the nvidia drivers..

---

### Post by duminas on 2005-08-13
My video card is an nVidia GeForce FX 5500.
My monitor is a CRT--specifically, an eView 15p, for which I can find no documents or anything.

**EDIT**
xorg removed. Please see the next post.

---

### Post by duminas on 2005-09-06
Posting to bump and continue.
The nVidia drivers are installed, that is, xorg uses 'nvidia', but the refresh rate is still weirding out on me. During both the nVidia logo and GDM login, that bright white line persists down the right side of the screen, and the bouncing of the screen stays around.

My *xorg.conf* from the prior post has been removed, and it can be found below:
```
[size=2]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
[b]	Option "HSync2"	"58.00"
	Option "VRefresh2"	"60.00"[/b]
EndSection

Section "Monitor"
	Identifier	"15 COLOR"
	Option		"DPMS"
[b]	HorizSync	30-58
	VertRefresh	50-120[/b]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"15 COLOR"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection[/size]
```I bolded things I added that I thought might make it work, but still no.

It goes back to normal after I pass the login step and get to the desktop itself.
Thanks for any continued assistance, guys.

---

