---
title: "Video card problem"
date: 2005-12-26
forum: Desktop Environments
---

### Post by davidswe on 2005-12-26
I changed my video card from a GeForce 5900 to an ATI based card. Now, the Xserver won't start. I'm sure I should have edited the xorg.conf file before changing. I didn't. Can anyone help me out of this mess? I am a relatively new linux user.

davidswe

---

### Post by 23meg on 2005-12-26
Please post your xorg.conf file and the exact model of your ATI card.

---

### Post by davidswe on 2005-12-26
The video card is an ATI Radeon 9600 Pro. How do I post the xorg.conf file? I can't load Ubuntu. Can you instruct me?

---

### Post by 23meg on 2005-12-26
Did you install the ATI fglrx drivers? Do a forum search for instructions on how to do that if you haven't. 

If you're connecting to the net via Windows, you can use a driver such as [Ext2 IFS]("http://www.fs-driver.org/") to mount your Linux partition under Windows to access the file /etc/X11/xorg.conf.

---

### Post by davidswe on 2005-12-26
Here is my xorg.conf; I think I see what is wrong. How do I edit it?

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

Section "Module"
	Load	"GLcore"
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
	Identifier	"NVIDIA Corporation NV35 [GeForce FX 5900]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"S/M 955SL"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900]"
	Monitor		"S/M 955SL"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

---

### Post by 23meg on 2005-12-26
Can you boot to a command prompt? If so, type ```
sudo nano /etc/X11/xorg.conf
``` to edit it. You should be able to run X if you change your "Driver" line to "ati", which is the open source ATI driver. I haven't installed the proprietarty ATI drivers myself so I can't help you with that if that's what you want to do but if you do a forum search you'll find instructions.

(Note: sorry for misreading your first post, which puzzled me about where exactly your problem was)

---

### Post by davidswe on 2005-12-26
I corrected my problem by running  *sudo dpkg-reconfigure -phigh xserver-xorg* to reconfigure the xserver. Once I had done this, I restarted normally and everything worked fine. Thanks for your help and suggestions, 23MEG.

davidswe

---

