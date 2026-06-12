---
title: "Dual monitors and ATI"
date: 2005-07-07
forum: Desktop Environments
---

### Post by JLTB on 2005-07-07
Hi Everyone,

I've been using ubuntu / kubuntu for a while now but it's my first post here.  I'll begin by saying thanks for the great software.  Ubuntu is by far the best desktop distro I've used, and I've tried a lot...

Well, with quite a few hours of fiddling I have managed to get my ATI Radeon 9600XT to accept two monitors (NEC 19" and 17") at the same time, DVI and RGB (HORRAY!).  Of course, being a typical linux geek I must now find a way to make it better.....

Currently I'm running in "big desktop" mode (from the fglrxconfig) since I need the ability to switch between windows.  This works alright, but it isn't as nice as I would like.

Does anyone have any tips, tricks, hacks, etc. to solve/help the following issues.

* Everything appears right in the centre of the screen (KDM login, new windows .. etc)
* Windows maximize across both monitors (I'd rather have them "stick" to the monitor they are on)
* Full screen movies stretch out across both monitors.
* Other such problems stemming from the merged screen in the xorg.conf setup.

Any advice would be great!

---

### Post by varunus on 2005-07-07
I'm not sure if this is different for ATI cards or not, but do you have Xinerama enabled?  Xinerama should fix a lot of the problems you're having (with stuff appearing in the middle, windows maximizing to both screens), but I'm not sure if it works with the ATI driver.  To try it out, open your /etc/X11/xorg.conf with "sudo gedit" and add the line
```
Option "Xinerama" "On"
``` 
to your "ServerFlags" section.

Good luck.

---

### Post by gammyhand on 2005-07-07
[QUOTE=varunus]I'm not sure if this is different for ATI cards or not, but do you have Xinerama enabled?  Xinerama should fix a lot of the problems you're having (with stuff appearing in the middle, windows maximizing to both screens), but I'm not sure if it works with the ATI driver.  To try it out, open your /etc/X11/xorg.conf with "sudo gedit" and add the line
```
Option "Xinerama" "On"
``` 
to your "ServerFlags" section.

Good luck.[/QUOTE]
 varunus this does NOT work for ATI cards. Or at least not my 9800 pro which crashed in a particularly dramatic and messy way :)

---

### Post by JLTB on 2005-07-07
Hi varunus and gammyhand, thanks for your replies.

As far as I know xinerama doesn't work with ATI drivers.  At best, from what I hear, it will disable DRI for your card (i.e.: no 3D GFX :().  At worst, it will break X.

I heard an elusive rumour (i can't remember where) about some merged FB setting that can allow ATI cards to behave better with dual monitors.  I have no idea if/how this works/exists.

I'll keep hunting ..... more posts welcome though!

---

### Post by gammyhand on 2005-07-07
[QUOTE=JLTB]Hi varunus and gammyhand, thanks for your replies.

As far as I know xinerama doesn't work with ATI drivers.  At best, from what I hear, it will disable DRI for your card (i.e.: no 3D GFX :().  At worst, it will break X.

I heard an elusive rumour (i can't remember where) about some merged FB setting that can allow ATI cards to behave better with dual monitors.  I have no idea if/how this works/exists.

I'll keep hunting ..... more posts welcome though![/QUOTE]
 I think I heard of that too. But I think it only gives you 2d accelaration.

---

### Post by autocrosser on 2005-07-11
[QUOTE=gammyhand]I think I heard of that too. But I think it only gives you 2d accelaration.[/QUOTE]

You can use Xinerama with ATI cards--you only get 2D acceleration with Xinerama enabled--the windows do "stick" at the last place you put them---If you are not a "hardcore" gamer--this option works well--the other problem is that both screens have to be "locked" to the same setting--I use 1024x768 for both my flats--the RandR extension Will Not Work---I started using Xinerama with YellowDog 4.0 and find I can not live without it (I do graphic design), but I only do "light" gaming in Linux--I boot up OSX if I want to play Unreal or Doom :-| ---

If you want an example of my Xorg.conf--I'll post it--

Anyone know if there is a gui for runlevel editing??


Cheers!!
Dean

---

### Post by gammyhand on 2005-07-12
[QUOTE=autocrosser]You can use Xinerama with ATI cards--you only get 2D acceleration with Xinerama enabled--the windows do "stick" at the last place you put them---If you are not a "hardcore" gamer--this option works well--the other problem is that both screens have to be "locked" to the same setting--I use 1024x768 for both my flats--the RandR extension Will Not Work---I started using Xinerama with YellowDog 4.0 and find I can not live without it (I do graphic design), but I only do "light" gaming in Linux--I boot up OSX if I want to play Unreal or Doom :-| ---

If you want an example of my Xorg.conf--I'll post it--

Anyone know if there is a gui for runlevel editing??


Cheers!!
Dean[/QUOTE]
 Some more advice would be great please autocrosser! I am not bothered about 3d performance in ubuntu. I am bothered about my login dialog being right in the middle of my two screens. My screens are identical models so running them both at 1280x1024 is no problem :)

---

### Post by gammyhand on 2005-07-15
[QUOTE=gammyhand]Some more advice would be great please autocrosser! I am not bothered about 3d performance in ubuntu. I am bothered about my login dialog being right in the middle of my two screens. My screens are identical models so running them both at 1280x1024 is no problem :)[/QUOTE]
Anyone? Help....this is depressing.

---

### Post by f20cap1 on 2005-07-15
[QUOTE=gammyhand]Anyone? Help....this is depressing.[/QUOTE]

Seeing as you are like me and care little about 3D acceleration, I'll post my xorg.conf in hopes that it may help you.

```

# Xorg configuration

Section "ServerLayout"
	Identifier     "Multihead layout"
	Screen      0  "Screen0" RightOf "Screen1"
	Screen      1  "Screen1" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Option	    "Xinerama" "on"
	Option	    "Clone" "off"
EndSection

Section "Files"
	RgbPath      "/usr/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	FontPath     "/usr/share/fonts/misc/"
	FontPath     "/usr/share/fonts/Speedo/"
	FontPath     "/usr/share/fonts/Type1/"
	FontPath     "/usr/share/fonts/corefonts/"
	FontPath     "/usr/share/fonts/CID/"
	FontPath     "/usr/share/fonts/TTF/"
	FontPath     "/usr/share/fonts/truetype/"
	FontPath     "/usr/share/fonts/lfp-fix/"
	FontPath     "/usr/share/fonts/75dpi/"
	FontPath     "/usr/share/fonts/100dpi/"
EndSection

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "fbdevhw"
	Load  "glx"
	Load  "record"
	Load  "freetype"
	Load  "type1"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Compaq"
	ModelName    "1825"
	DisplaySize  360	290
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
	Option	    "dpms"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Compaq"
	ModelName    "1825"
	DisplaySize  360	290
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "radeon"
	VendorName  "Videocard vendor"
	BoardName   "ATI FireGL X1"
EndSection

Section "Device"
	Identifier  "Videocard1"
	Driver      "radeon"
	VendorName  "Videocard Vendor"
	BoardName   "ATI FireGL X1"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Videocard1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection

```

Take a look at that and see if it helps.

Just to note, my primary display is on the right.  Adjust the config accordingly :)

---

### Post by gammyhand on 2005-07-16
[QUOTE=f20cap1]Seeing as you are like me and care little about 3D acceleration, I'll post my xorg.conf in hopes that it may help you.

```

# Xorg configuration

Section "ServerLayout"
	Identifier     "Multihead layout"
	Screen      0  "Screen0" RightOf "Screen1"
	Screen      1  "Screen1" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Option	    "Xinerama" "on"
	Option	    "Clone" "off"
EndSection

Section "Files"
	RgbPath      "/usr/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	FontPath     "/usr/share/fonts/misc/"
	FontPath     "/usr/share/fonts/Speedo/"
	FontPath     "/usr/share/fonts/Type1/"
	FontPath     "/usr/share/fonts/corefonts/"
	FontPath     "/usr/share/fonts/CID/"
	FontPath     "/usr/share/fonts/TTF/"
	FontPath     "/usr/share/fonts/truetype/"
	FontPath     "/usr/share/fonts/lfp-fix/"
	FontPath     "/usr/share/fonts/75dpi/"
	FontPath     "/usr/share/fonts/100dpi/"
EndSection

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "fbdevhw"
	Load  "glx"
	Load  "record"
	Load  "freetype"
	Load  "type1"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Compaq"
	ModelName    "1825"
	DisplaySize  360	290
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
	Option	    "dpms"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Compaq"
	ModelName    "1825"
	DisplaySize  360	290
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "radeon"
	VendorName  "Videocard vendor"
	BoardName   "ATI FireGL X1"
EndSection

Section "Device"
	Identifier  "Videocard1"
	Driver      "radeon"
	VendorName  "Videocard Vendor"
	BoardName   "ATI FireGL X1"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Videocard1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection

```

Take a look at that and see if it helps.

Just to note, my primary display is on the right.  Adjust the config accordingly :)[/QUOTE]
 right....I will give that a go in a bit. I would like 3d support to be honest, but I am not gaming so it is not important. Just annoys me that I can't get any 3d screensavers working.

---

### Post by gammyhand on 2005-07-16
[QUOTE=gammyhand]right....I will give that a go in a bit. I would like 3d support to be honest, but I am not gaming so it is not important. Just annoys me that I can't get any 3d screensavers working.[/QUOTE]
 I tried using the config from your xorg file and x would not start so I had to revert to my backup file. :(

---

### Post by gammyhand on 2005-07-18
[QUOTE=gammyhand]I tried using the config from your xorg file and x would not start so I had to revert to my backup file. :([/QUOTE]
 Anyone got any thoughts on this? I can't afford to have a redundant monitor :(

---

### Post by autocrosser on 2005-07-21
I'm sorry I have not got back to you---I race on the West Coast & needed to get a car ready for this weekend :grin: ---In any case---

What I use is FBmerged--I tried Xinerama & found the FPS to be well under 75 per :-x --FBmerged allows DRI to be enabled--I still don't have it tuned good enough, but---

SO-take a look at this xorg.conf---

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
# again, run the following commands:
#
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
      SubSection  "extmod"
        Option    "omit xfree-dga"
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
	Option		"ChordMiddle"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Monitor"
        DisplaySize  376.32  301.056
	Identifier   "VL1918"
	ModelName    "VL1918"
	VendorName   "Princeton"
	HorizSync    31.0 - 79.0
	VertRefresh  60.0 - 75.0
	Option	     "DPMS"
EndSection

Section "Monitor"
        DisplaySize  304.1  228.1 
        Identifier   "L152"
        ModelName    "L152"
        VendorName   "Sylvania"
        HorizSync    30.0 - 60.0
        VertRefresh  60.0 - 75.0
        Option       "DPMS"
EndSection

Section "Device"
        Identifier "Radeon 9600"
        Driver     "radeon"
        VendorName  "ATI"
        BoardName   "ATI Radeon 9600 AP (AGP)"
        BusID       "PCI:0:16:0"
        VideoRam    65536
        Option      "MergedFB"                  "True"
        Option      "AGPMode"            	"4"
        Option      "AGPFastWrite"       	"true"
        Option      "CRT2HSync"                 "31.5 - 60.0"
        Option      "CRT2VRefresh"              "60-75"
        Option      "MonitorLayout"             "LCD,CRT" #use LCD,CRT even if you have 2 CRTs
        Option      "OverlayOnCRTC2"            "true"
        Option      "MetaModes"                 "1024x768-1024x768"
        Option      "CRT2Position"              "RightOf"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Radeon 9600"
	Monitor    "VL1918"
	DefaultDepth     24
	SubSection "Display"
		Depth     8
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768"

	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Radeon 9600"
	Monitor    "L152"
	DefaultDepth     24
	SubSection "Display"
		Depth     8
		Modes    "1024x768"
	EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1024x768"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1024x768"
        EndSubSection

EndSection

Section "ServerLayout"
	Identifier	"Main Layout"
	Screen          "Screen0" LeftOf "Screen1"
        Screen          "Screen1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        
EndSection

Section "DRI"
	Mode	0666
EndSection


Cheers!!
Dean

---

### Post by gammyhand on 2005-07-22
Does that setup stop dialog boxes appearing in the middle of both screens though?

---

### Post by autocrosser on 2005-07-23
Most apps seem to observe placement--I have one game (Enigma) that centers--but most important apps "seem" to stick where I want them (as I read the info-"newer" apps are "aware")--glgears reports about 250fps :-? --not good, but with Xinerama, I was not even getting 100fps--The other thing is FBMerged supports RandR change--It took me several shots at the xorg to get it working right, so I'd use mine as a starting point & play 'round with it.

As the saying does--"your mileage may vary"


Cheers!!
Dean

---

