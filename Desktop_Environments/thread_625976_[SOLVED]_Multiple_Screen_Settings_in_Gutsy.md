---
title: "[SOLVED] Multiple Screen Settings in Gutsy"
date: 2007-11-28
forum: Desktop Environments
---

### Post by jbt on 2007-11-28
I have an ATI Radeon 7000 graphics card, with 2 monitors (one from analogue, and one from DVI)

I have finally figured out how to get dual screen working.

Despite many sample ATI configs with Xinerama and MergedFB, it seems that for the 7000 the only way is to use xrandr, and I now have this working (ish).

My problem is that the DVI screen is really washed out.
No amount of adjustment on the monitor helps, but reducing the Gamma in xorg.conf does help a bit.

The problem is that with xrandr, there does not seem to be a way to set the Gamma for each monitor seperately, or if there is I cant find a way.

The relevant chunk from my xorg.conf is below.
I have also tried adding Screen 2 into server layout, but it has no effect.

The DisplaySize lines have no effect either.
I have to use xrandr to set 96 dpi manually.

And finally Desktop effects seem to have stopped working now that I have two screens.

Anyone have any ideas ?

Thanks
JohnT

Section "Device"
	Identifier	"ATI Radeon"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Vendorname	"ATI"
	Option "Monitor-DVI-0" "DVI Monitor"
	Option "Monitor-VGA-0" "VGA Monitor"
	Option		"MergedFB"	"on"
	Option		"UseFBDev"		"true"
  	Option      "AGPFastWrite"  "on"
        Option      "DynamicClocks" "on"
        Option      "ColorTiling"   "on"
EndSection

Section "Monitor"
	Identifier	"DVI Monitor"
	Vendorname	"SamSung"
	Modelname	"920N"
	Gamma	0.6
   	Option "RightOf" "VGA Monitor"
	DisplaySize	338	270	# 1280x1024 96dpi
EndSection

Section "Monitor"
	Identifier	"VGA Monitor"
	Vendorname	"SamSung"
	Modelname	"920N"
	Gamma	1.0
	DisplaySize	338	270	# 1280x1024 96dpi
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI Radeon"
	Monitor		"VGA Monitor"
	Defaultdepth	16
	SubSection "Display"
		 Depth	16
		Virtual	2560	1024
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen2"
	Device		"ATI Radeon"
	Monitor		"DVI Monitor"
	Defaultdepth	16
	SubSection "Display"
		 Depth	16
		Virtual	2560	1024
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0 "Screen1" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

---

### Post by jbt on 2007-11-29
> **jbt said:**
> I have an ATI Radeon 7000 graphics card, with 2 monitors (one from analogue, and one from DVI)
And finally Desktop effects seem to have stopped working now that I have two screens.

EndSection

I have now figured this bit out.
It seems that compiz only supports screens upto 2048x2048

If I reduce my screens to 2 x 1024x768 the effects start working again !

Regards
JohnT

---

### Post by jbt on 2007-12-04
> **jbt said:**
> I have an ATI Radeon 7000 graphics card, with 2 monitors (one from analogue, and one from DVI)

I have finally figured out how to get dual screen working.

Despite many sample ATI configs with Xinerama and MergedFB, it seems that for the 7000 the only way is to use xrandr, and I now have this working (ish).

My problem is that the DVI screen is really washed out.
No amount of adjustment on the monitor helps, but reducing the Gamma in xorg.conf does help a bit.



OK - I have now discovered that this is a bug in the ati driver:
[https://bugs.freedesktop.org/show_bug.cgi?id=1082](https://bugs.freedesktop.org/show_bug.cgi?id=1082)


Can someone please explain how I get hold of the latest ati driver, and install it ?

Thanks
JohnT

---

### Post by jbt on 2007-12-06
> **jbt said:**
> OK - I have now discovered that this is a bug in the ati driver:
[https://bugs.freedesktop.org/show_bug.cgi?id=1082](https://bugs.freedesktop.org/show_bug.cgi?id=1082)


Can someone please explain how I get hold of the latest ati driver, and install it ?

Thanks
JohnT

Found the answer myself now:

Lots of useful X related stuff here:
[https://wiki.ubuntu.com/X](https://wiki.ubuntu.com/X)

Which pointed me to these pages with the latest ATI driver details:

[https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

[https://launchpad.net/~tormodvolden/+archive](https://launchpad.net/~tormodvolden/+archive)

Regards
JohnT

---

### Post by rou on 2007-12-18
Hi,

I have a Radeon RV100 QY [7000/VE] and I'm finding it difficult to have dual screen on Gnome after upgrading to Gutsy. I have tried most of the possible configurations, included xrandr, but I have no success. 

I have two 17'' screens attached to the analog VGA ports of the card. Terminal mode clones the two monitors, but when I startx one of them goes off. Xrandr only detects one of the monitors conected.

See xrandr, lspci and xorg.conf output: Any Help or Idea??



$ xrandr -q

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024

VGA-0 connected 1280x1024+0+0 (normal left inverted right) 0mm x 0mm

   1600x1024      60.0  

   1280x1024      59.9*    60.0  

   1280x1024@60   60.0  

   1440x900       60.2  

   1280x960       60.0     59.9  

   1280x960@60    60.0  

   1280x800       60.0  

   1152x864@75    75.0  

   1152x864       75.0     60.0  

   1280x768       60.0  

   1152x768       54.8  

   1024x768@70    70.1  

   1024x768       70.1     60.0     59.9  

   1024x768@60    60.0  

   832x624@75     74.6  

   832x624        74.6     59.8  

   800x600@72     72.2  

   800x600        72.2     75.0     60.3     59.9     56.2  

   800x600@75     75.0  

   800x600@60     60.3  

   800x600@56     56.2  

   640x480@72     72.8  

   640x480@75     75.0  

   640x480        72.8     75.0  

   640x480@60     60.0  

DVI-0 disconnected (normal left inverted right)

S-video disconnected (normal left inverted right)

]0;rou@workstation: ~rou@workstation:~$ lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge

00:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)

00:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

]0;rou@workstation: ~rou@workstation:~$ 

]0;rou@workstation: ~rou@workstation:~$ 

]0;rou@workstation: ~rou@workstation:~$ cat /etc/X11/xorg.conf

# xorg.conf (xorg X Window System server configuration file)

#

# This file was generated by dexconf, the Debian X Configuration tool, using

# values from the debconf database.

#

# Edit this file with caution, and see the xorg.conf manual page.

# (Type "man xorg.conf" at the shell prompt.)

#

# This file is automatically updated on xserver-xorg package upgrades *only*

# if it has not been modified since the last upgrade of the xserver-xorg

# package.

#

# If you have edited this file but would like it to be automatically updated

# again, run the following command:

#   sudo dpkg-reconfigure -phigh xserver-xorg



Section "Files"

EndSection



Section "InputDevice"

	Identifier	"Generic Keyboard"

	Driver		"kbd"

	Option		"CoreKeyboard"

	Option		"XkbRules"	"xorg"

	Option		"XkbModel"	"pc105"

	Option		"XkbLayout"	"es"

	Option		"XkbOptions"	"lv3:ralt_switch"

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

	Identifier	"ATI Radeon"

	Boardname	"ATI Radeon"

	Busid		"PCI:1:0:0"

	Driver		"ati"

	Screen	0

	Vendorname	"ATI"

	Option		"MergedFB"	"off"

EndSection



Section "Monitor"

	Identifier	"DVI Monitor"

	Vendorname	"SamSung"

	Modelname	"920N"

	Gamma	0.6

	Option		"RightOf"	"VGA Monitor"

	Displaysize	338	270# 1280x1024 96dpi

EndSection



Section "Monitor"

	Identifier	"VGA Monitor"

	Vendorname	"Generic CRT Display"

	Modelname	"Monitor 1280x1024"

	Horizsync	31.5-81.0

	Vertrefresh	50-75

  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync

  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync

  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync

  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync

  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync

  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync

  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync

  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync

  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync

  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync

  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync

  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync

  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync

  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync

  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync

  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync

  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync

  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync

	Gamma	1.0

EndSection



Section "Screen"

	Identifier	"Screen1"

	Device		"ATI Radeon"

	Monitor		"VGA Monitor"

	Defaultdepth	16

	SubSection "Display"

		Depth	16

		Virtual	2560	1024

		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"832x624@75"	"1600x1200@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"

	EndSubSection

EndSection



Section "Screen"

	Identifier	"Screen2"

	Device		"ATI Radeon"

	Monitor		"DVI Monitor"

	Defaultdepth	16

	SubSection "Display"

		Depth	16

		Virtual	2560	1024

	EndSubSection

EndSection

Section "ServerLayout"

	Identifier	"Default Layout"

  screen 0 "Screen1" 0 0

	Inputdevice	"Generic Keyboard"

	Inputdevice	"Configured Mouse"

EndSection

Section "Module"

	Load		"glx"

	Load		"GLcore"

	Load		"dri"

	Load		"v4l"

EndSection

Section "ServerFlags"

EndSection

---

### Post by rou on 2007-12-19
Hello JohnT,

Doing progress, the following command connected the DVI-0 attached monitor:

xrandr --output DVI-0 --set load_detection 1

and 

xrandr --output DVI-0 --mode 1280x1024

woke it up.

Now I have a clone of the VGA-0 monitor in the DVI-0, and

xrandr --output DVI-0 --right-of VGA-0

expanded my desktop again to both monitors... !!!

Now the question is: will this configuration remain if I reboot X or the machine??? If not: which xorg.conf tags will set this parameters back again so I won't have to retype them on every session???

I'll see if I find the answer and keep you posted, and also the forum...

Thank's for your links

---

### Post by jbt on 2007-12-20
> **rou said:**
> Hello JohnT,

Doing progress, the following command connected the DVI-0 attached monitor:

xrandr --output DVI-0 --set load_detection 1

and 

xrandr --output DVI-0 --mode 1280x1024

woke it up.

Now I have a clone of the VGA-0 monitor in the DVI-0, and

xrandr --output DVI-0 --right-of VGA-0

expanded my desktop again to both monitors... !!!

Now the question is: will this configuration remain if I reboot X or the machine??? If not: which xorg.conf tags will set this parameters back again so I won't have to retype them on every session???

I'll see if I find the answer and keep you posted, and also the forum...

Thank's for your links

Not sure why xorg.conf is not doing this for you, but if you find that you cannot get it to happen, you can put your xrandr commands in your gdm startup. 

I use it to add my screen resolution, as xorg.conf isn't working for me.
I have added:
[INDENT]xrandr --dpi 100[/INDENT]

to the end of:
[INDENT]/etc/gdm/Init/Default[/INDENT]

---

### Post by vladone on 2008-06-06
I am looking for a savvy partner in an art video multiple screen system start-up.
Sorry if this is not the right place for this topic, thank you in advance for your response.

---

