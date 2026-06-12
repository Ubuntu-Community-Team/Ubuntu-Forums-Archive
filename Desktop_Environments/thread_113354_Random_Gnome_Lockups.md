---
title: "Random Gnome Lockups"
date: 2006-01-06
forum: Desktop Environments
---

### Post by bagel on 2006-01-06
Hello there;
 
I'm running Ubuntu Breezy on my Sony Vaio PCG-K215Z Notebook, and it is working great, except that I have random lockups(1-2 per day) in Gnome. 
A lockup means in my case that suddenly I can't move the mouse cursor anymore and the whole screen is frozen(with the picture it last displayed). No screensaver is starting, no unusual CPU activity(fan sound normal). I also can't ping my machine over the network. The only way out is pressing the power button... The lockups seem not to prefer any application and also occur while I'm not at the machine.

I also noticed that sometimes the external USB-mouse I use stops working, but I'm still able to use touchpad. When I re-plug the external mouse, system continues to work normal. I just mention this, in case the problem is not graphics related.

Graphics: Ati Mobility Radeon 9200
P4-3.06GHz, 512 MB-RAM

Hoping that someone might be able to help, this is really getting annoying,
Greetings,
Bagel

Here my xorg.con file:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
# ...
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

Section "Module"  #Uncommented to test if it would resolve my problem
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
#	Load	"glx"
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
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 M9+ (RV250)"
#	Driver		"ati"     #Tested to see if this would resolve my problem
	Driver 		"radeon"	
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 M9+ (RV250)"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

#Section "DRI"         #Uncommented to see if it helps
#	Mode	0666
#EndSection


```

---

### Post by bonsiware on 2006-01-06
I solved this problem installing linux-686, the kernel for i686 architectures

---

### Post by bagel on 2006-01-06
Exactly this problem? 

hmm.. I compiled my kernel manually and selected "Pentium-4M" as processor family but I'll try anyway (-;

Thanks, 
bagel

---

### Post by bonsiware on 2006-01-06
If you compiled in that way, then I think it's the same... but you could try anyway...

bye

---

### Post by bagel on 2006-01-06
Ok, I'm now running the Kernel you suggested.. Let's hope it works :)  

Ciao, bagel

---

