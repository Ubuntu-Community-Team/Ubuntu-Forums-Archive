---
title: "Direct Rendering Snaffu!!"
date: 2008-02-15
forum: Desktop Environments
---

### Post by carnivore1 on 2008-02-15
Hey All,

after Days of trying to get Direct Rendering working on Ubuntu 7.1 without success i finally gave up and did a fresh install of Ubuntu 7.1 and it worked again!! 

to be sure it was working i ran the following in a terminal: "glxinfo | grep -i direct"

this returned a yes and i though i was in the clear. once i was sure i had my big issue taken care of finally i did what any good newb would do and went strait for my pretties

thats right, i enabled desktop effects and ran insatlled xserver-xgl so i could get the cool cube effect going. i did this by using the following line in the terminal: "sudo apt-get install xserver-xgl".

once done i did a restart and guess what. MY DIRECT RENDERING IS NOT WORKING AGAIN!!!!

when i run this line in a terminal: "glxinfo | grep -i direct". I get the following responce:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


some one please help im going crazy here.

---

### Post by kdub432 on 2008-02-15
We will need more info than this. Please post the contents of /etc/X11/xorg.conf , along with the make and model of your graphics card

---

### Post by carnivore1 on 2008-02-15
> **kdub432 said:**
> We will need more info than this. Please post the contents of /etc/X11/xorg.conf , along with the make and model of your graphics card

Hey kdub, 

thanks for the reply. i am currently using NVIDIA GeForce Go 7300/PCI/SSE2 Card on a DELL Inspiron E1505 Laptop. and the etc/X11/xorg.conf file reads as follows:

[COLOR="Navy"]Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-84
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection[/COLOR]

Any suggestions??

---

### Post by carnivore1 on 2008-02-16
anyone have any ideas at all???

as it stands now, i can have my desktop effects, OR i can have a functional video card thats capable of direct rendering.

I have found a few other places where people are having exactly the same issue as i am but no one so far has come up with a resolution.

---

### Post by cammin on 2008-02-17
add

** Load "dri"**

to the **"Module"** section

Usually there's more than GLX in that section, If you have an old copy of your xorg.conf file, you should compare the two and see what else is missing.

---

