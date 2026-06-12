---
title: "Laptop randomly freezes..."
date: 2005-12-07
forum: General Help
---

### Post by harty83 on 2005-12-07
Hello,

I'm in need of some help here.  I have a Dell Inspiron 5150 laptop that I have installed Ubuntu breezy on.  I'm a newby to Linux so please have patient with me.

My laptop seems to be randomly locking up to where I am forced to manually shut it down (by holding down the power button).  I have no clue as to where to start in figuring this thing out.  

Here are some "need to knows" to start with.

I have a custom kernel installed (patched with Suspend2) using the howto: [http://ubuntuforums.org/showthread.php?t=75443](http://ubuntuforums.org/showthread.php?t=75443)

I also have installed Nvidia's drivers using this howto (to be able to have both Suspend2 and Nvidia's drivers): [http://ubuntuforums.org/showthread.php?t=79295](http://ubuntuforums.org/showthread.php?t=79295)

I use ndiswrapper to get my broadcom wireless card to work.

The freeze ups tend to occur when I'm using either Firefox 1.5, Synaptic or Evolution.  

What other information do you need to know to begin assessing this problem?

Also, there has been a couple times that I have resumed from hibernation and my pc freezes with a black screen and my caps lock and arrow lock lights flash.  Again I have to do a hard boot.  Could the two be related?  Is my pc possessed?  :-) 

Oh by the way I LOVE LINUX!!! I became so pissed at winblows two weeks ago that  I reformated my laptop and installed ubuntu as my main OS.  I am using VMware to run winblows for those few programs that wine won't run.  I feel so free now ;-)  I eagerly look forward to the day that I can be COMPLETELY free from all MS and winblows dependent programs.

---

### Post by rubinstein on 2005-12-08
There are known problems with nvidia's proprietary driver. See [http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14) for lots of postings about lockups, I have the "screen frozen, but mouse pointer moves" bug [http://www.nvnews.net/vbulletin/showthread.php?t=31858](http://www.nvnews.net/vbulletin/showthread.php?t=31858) Unfortunately there is no solution yet because these are proprietary drivers, they are not open source.

I suggest you use the free software "nv" driver to see if the proprietary nvidia driver is the problem. Best thing is always to test the computer step by step. If the nvidia driver is not the problem, then move on to test the next component :-)

---

### Post by harty83 on 2005-12-10
Definitely the nvidia drivers so I've gone back to the nv drivers.  The only real reason I use the nvidia drivers is because I like to use an external monitor attached to my laptop.  However using the nv drivers, when I switch to the external, my laptop's display goes black, but nothing happens on the external.  Then when I switch back, its as if half the screen is missing and the half that is present is centered on the laptop's display.    Can I set up the xorg.conf in a way to get it to work when I switch to the external monitor?  I'm sure I can, but I'm a newby and not familiar with the xorg.conf options.  

When I press the monitor's menu button it says at the bottom "44k / 55hz" and "For best results use 1024x768"

Here is my xorg.conf file

```
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
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
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
#	Option		"NvAgp" "1"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

