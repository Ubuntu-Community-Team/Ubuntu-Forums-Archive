---
title: "fglrx 8.14.13 and no 3D"
date: 2005-06-09
forum: Desktop Environments
---

### Post by sunscape on 2005-06-09
Now I know what you are going to say... "the answers are in the forums" and "follow the guide it is easy!" And the following--->

agpgart = no
check if the module is loaded
............

But these are not the remedy for my problem that seems to have become a plague.

You see, my 3d does not work... and I have no clue! It shoudl be easy! right? Just use the new installer from ATI
.......................
fglrxinfo:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

.......................
X log:
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON 9600 SE (RV350 4151) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Option "AGPMode" is not used
(WW) fglrx(0): Option "AGPFastWrite" is not used
(WW) fglrx(0): Option "EnablePageFlip" is not used
(WW) fglrx(0): Option "AllowGLXWithComposite" is not used
......................
xorg.conf file

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

Section "Extensions"
	Option 	"Composite" "Enable"
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
	Identifier	"ATI Technologies, Inc. Radeon 9600 SE (RV350 AQ)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "True"
	Option		"EnablePageFlip" "True"
	Option          "backingstore" "true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"Avitron"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 SE (RV350 AQ)"
	Monitor		"Avitron"
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
EndSection

Section "DRI"
	Mode	0666
EndSection


Anyone got a solution? I think i need the biggest linux nerd on the planet for this one :-P

---

### Post by sapo on 2005-06-09
This isnt the place to ask question..

btw.. try removing the xorg-fglrx and the linux-restricted-modules before installing the new driver...

Here it worked in the first attemp :p

---

### Post by matthew on 2005-06-10
Hi, Sunscape,

I haven't installed the new drivers yet, but I had the same problem while installing the previous version. Take a look at the last post in this thread: [http://www.ubuntuforums.org/showthread.php?t=39704&highlight=ati+9700](http://www.ubuntuforums.org/showthread.php?t=39704&highlight=ati+9700)

I'm wondering if you need to stop the xserver when you install the new drivers.

Hey, wait. The new driver comes with an actual graphic installer program, doesn't it? Hmm.. Sorry, I don't think my suggestion is worth much other than ruling something out as a problem.

I know this gets frustrating sometimes...hang in there, you will figure it out!

---

### Post by sunscape on 2005-06-10
Sollution!

Hey!

I think i got it fixed and it works on my system. You need to check your kernel restriced modules and headers to be certain that they match your kernel. Then use the below command. (Be certain you have build-essential installed with all dependencies)

--I installed and then completely removed the fglrx drivers from synaptic to be certain that they were gone.

Then i did this for safety sake

sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME

Afterward I just ran the ati installer, ran fglrxconfig, and it worked after restarting.

---

