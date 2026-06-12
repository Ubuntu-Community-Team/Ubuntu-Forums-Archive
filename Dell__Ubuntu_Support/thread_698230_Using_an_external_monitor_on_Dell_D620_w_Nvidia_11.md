---
title: "Using an external monitor on Dell D620 w Nvidia 110M"
date: 2008-02-16
forum: Dell  Ubuntu Support
---

### Post by TaylorMarieXXX on 2008-02-16
Hey guys, I came to this forum looking for a way to get my external monitor working with the Nvidia 110M on my Dell D620.  I encountered a ton of problems, but got enough help that I was able to figure it out.  So I figure in the future I will be needing help but I will pay it forward.  The whole thread can be found at [http://ubuntuforums.org/showthread.php?p=4340828#post4340828]("http://ubuntuforums.org/showthread.php?p=4340828#post4340828")
I just posted this so it could be searched and found under the proper header in the proper forum.  Here is the short of it.

Remove the application under administartion "Screen settings" or whatever it's called.

Make sure the Nvidia Driver is enabled under the restricted drivers.

Now that you removed that configuration app that does nothing but clutter up your xorg.conf, you need to create a new clean one using "sudo dpkg-reconfigure -phigh xserver-org"  It may bring up this little text based questionaire thing but just keep choosing the defaults and it will auto detect everything.

Now all you have to do is add two lines to your xorg, and edit it for the resolution you want.  Below is my working xorg, the lines added were the two that say "option twinview"

And there you go.  It's a good place to start and it works with my Dell D620 laptop and Acer AL2216W monitor.

Section "Files"
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
	Option		"TwinView"	"on"
	Option		"TwinViewOrientation"	"clone"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-72
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
EndSection

---

