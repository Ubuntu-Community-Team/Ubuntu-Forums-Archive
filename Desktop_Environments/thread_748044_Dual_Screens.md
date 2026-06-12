---
title: "Dual Screens"
date: 2008-04-07
forum: Desktop Environments
---

### Post by kippi on 2008-04-07
Hey, 

I am using hardy 8.04, so not sure if this is a bug with hardy or a bug with my x config. I know hardy is in beta!! But if it something I have done wrong and I can fix it then that would be a great help.

I am trying to lock the screen using Ctrl - L, the left screen is going black but the right screen isn't locking, When I want to come out of the lock I have to restart X.

Errors from syslog:

Apr  7 11:09:53 cowen-desktop kernel: [ 1337.245390] [fglrx:firegl_lock_free] *ERROR* lock was not held by 2! (*lock=0x80000001)
Apr  7 11:09:53 cowen-desktop kernel: [ 1337.245397] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!


My Xorg config:

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
  screen 1 "aticonfig-Screen[1]" rightof "aticonfig-Screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"dri"
	Load		"v4l"
	Load		"glx"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"off"
	Option		"Xinerama"	"true"
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
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	57.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Vendorname	"Dell"
	Modelname	"Dell 1704FPV (Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56.0-76.0
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

Section "Monitor"
	Identifier	"aticonfig-Monitor[1]"
	Vendorname	"Dell"
	Modelname	"Dell 1704FPV (Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56.0-76.0
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

Section "Device"
	Identifier	"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver		"fglrx"
	Option		"MonitorLayout"	"LCD, CRT"
	Option		"CRT2Position"	"RightOf"
	Option		"MetaModes"	"1280x1024-1280x1024"
	Option		"MergedNonRectangular"	"true"
	Option		"MergedFB"	"true"
	Option		"RenderAccel"	"true"
	# Option     "MergedXinerama" "on"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Device"
	Identifier	"aticonfig-Device[1]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"832x624@75"	"1600x1200@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[1]"
	Device		"aticonfig-Device[1]"
	Monitor		"aticonfig-Monitor[1]"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"832x624@75"	"1600x1200@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"
	Option		"Composite"	"0"
EndSection

Section "device" #  
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection

---

### Post by cprofitt on 2008-04-07
I actually suspect this might be a bug in the ATI driver... I have the same issue on Fedora 8 (which is not beta - but only with dual monitors).

---

### Post by kippi on 2008-04-08
Ah ok!!!

I will have a look around. The thing is this worked fine on Ubuntu 7.04

Many Thanks

---

### Post by siert on 2008-04-18
Exactly the same problem here after the upgrade from 7.04 to 8.

My kernel buffer log before the screen lock problem:
[   30.074529] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   30.074691] [fglrx] ASYNCIO init succeed!
[   30.075715] [fglrx] PAT is enabled successfully!
[   30.075854] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   42.534606] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[   42.534612] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   42.534615] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
[   42.534617] [fglrx] Reserve Block - 3 offset =  0Xffbf000 length = 0X40000
[   42.786978] [fglrx] interrupt source 10000000 successfully enabled
[   42.786984] [fglrx] enable ID = 0x00000008
[   42.786991] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   42.813236] [fglrx:firegl_lock_free] *ERROR* lock was not held by 2! (*lock=0x80000001)
[   42.813248] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!

My fglrx versions:

fglrx-control 1:8-3+2.6.24.12-16.34
fglrx-kernel-source 1:8-3+2.6.24.12-16.34
xorg-driver-fglrx 1:7.1.0-8-3+2.6.24.12-16.34

My kernel buffer log after the screenlock problem:

[ 1244.763874] [fglrx:firegl_cmmqs_CWDDE_32] *ERROR* CMMQS CWDDE32: pvDriver handle is not valid.
[ 1244.764009] [fglrx:firegl_cmmqs_CWDDE32] *ERROR* CMMQS CWDDE is failed: firegl_cmmqs_CWDDE32
[ 1244.764142] [fglrx:firegl_cmmqs_CWDDE_32] *ERROR* CMMQS CWDDE32: pvDriver handle is not valid.
[ 1244.764270] [fglrx:firegl_cmmqs_CWDDE32] *ERROR* CMMQS CWDDE is failed: firegl_cmmqs_CWDDE32
[ 1244.764395] [fglrx:firegl_cmmqs_CWDDE_32] *ERROR* CMMQS CWDDE32: pvDriver handle is not valid.
[ 1244.764523] [fglrx:firegl_cmmqs_CWDDE32] *ERROR* CMMQS CWDDE is failed: firegl_cmmqs_CWDDE32
[ 1244.764654] [fglrx:firegl_cmmqs_CWDDE_32] *ERROR* CMMQS CWDDE32: pvDriver handle is not valid.
[ 1244.764779] [fglrx:firegl_cmmqs_CWDDE32] *ERROR* CMMQS CWDDE is failed: firegl_cmmqs_CWDDE32
[ 1244.764929] [fglrx:firegl_cmmqs_CWDDE_32] *ERROR* CMMQS CWDDE32: pvDriver handle is not valid.
[ 1244.765056] [fglrx:firegl_cmmqs_CWDDE32] *ERROR* CMMQS CWDDE is failed: firegl_cmmqs_CWDDE32
[ 1244.765186] [fglrx:firegl_cmmqs_CWDDE_32] *ERROR* CMMQS CWDDE32: pvDriver handle is not valid.
[ 1244.765311] [fglrx:firegl_cmmqs_CWDDE32] *ERROR* CMMQS CWDDE is failed: firegl_cmmqs_CWDDE32
[ 1244.765440] [fglrx:firegl_cmmqs_CWDDE_32] *ERROR* CMMQS CWDDE32: pvDriver handle is not valid.
[ 1244.765565] [fglrx:firegl_cmmqs_CWDDE32] *ERROR* CMMQS CWDDE is failed: firegl_cmmqs_CWDDE32
[ 1244.765694] [fglrx:firegl_cmmqs_CWDDE_32] *ERROR* CMMQS CWDDE32: pvDriver handle is not valid.
[ 1244.765819] [fglrx:firegl_cmmqs_CWDDE32] *ERROR* CMMQS CWDDE is failed: firegl_cmmqs_CWDDE32
[ 1244.766505] [fglrx:firegl_cmmqs_CWDDE_32] *ERROR* CMMQS CWDDE32: pvDriver handle is not valid.
[ 1244.766631] [fglrx:firegl_cmmqs_CWDDE32] *ERROR* CMMQS CWDDE is failed: firegl_cmmqs_CWDDE32


Did not find a solution yet.

---

### Post by siert on 2008-04-18
I fixed the problem.

- Disable fglrx in the restricted driver manager
- Make sure /usr/lib/libGL.so.1 is linked to /usr/lib/libGL.so.1.2
- Install package dkms
- Install the ATI 8.4 driver

*Generate Ubuntu packages:*
[FONT="Courier New"]  sudo ./ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu/8.04[/FONT]

*Install Ubuntu packages:*
[FONT="Courier New"]  for i in xorg-driver-fglrx_8.476-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.476-0ubuntu1_i386.deb fglrx-amdcccle_8.476-0ubuntu1_i386.deb fglrx-kernel-source_8.476-0ubuntu1_i386.deb ; do dpkg -i $i ; done[/FONT]

*Optionally: restart.*

---

### Post by kippi on 2008-04-21
Ok,

I have done as the last reply said but still getting the same issue.

How can I check for a 100% that - Make sure /usr/lib/libGL.so.1 is linked to /usr/lib/libGL.so.1.2

Thanks for you help!!

Chris,

---

### Post by dda on 2008-04-26
Here is the command to check:

```
$ ls -l /usr/lib/libGL.so.1
lrwxrwxrwx 1 root root 28 2008-04-20 01:14 /usr/lib/libGL.so.1 -> /usr/lib64/xorg/libGL.so.1.2
```

- for me it is not linked exactly to as described, but you got the idea. And yes, I have the same problem with user switch. :(

---

### Post by seapahn on 2008-06-03
> **siert said:**
> I fixed the problem.

- Disable fglrx in the restricted driver manager
- Make sure /usr/lib/libGL.so.1 is linked to /usr/lib/libGL.so.1.2
- Install package dkms
- Install the ATI 8.4 driver

*Generate Ubuntu packages:*
[FONT="Courier New"]  sudo ./ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu/8.04[/FONT]

*Install Ubuntu packages:*
[FONT="Courier New"]  for i in xorg-driver-fglrx_8.476-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.476-0ubuntu1_i386.deb fglrx-amdcccle_8.476-0ubuntu1_i386.deb fglrx-kernel-source_8.476-0ubuntu1_i386.deb ; do dpkg -i $i ; done[/FONT]

*Optionally: restart.*

I have a similar problem but in my case, whenever trying to run any 3D apps (e.g. glxgears or screen savers) or mplayer on my second display the whole X system freezes. Following the suggestion above to disable fglrx in the restricted driver manager seems to revert to the mesa GL stuff (as reported by flgrxinfo) no matter what version of fglrx is installed ... which is not good.

This seems to be a bug in the 8.5 driver as well.

My setup:

Hardy 8.04
Catalyst fglrx 8.5 (tried 8.4 too)
Ati x1200 on a Asus M2A-VM motherboard
Dual head with HDMI being primary and DVI as secondary.

Error message in syslog followed by a complete X freeze (system still works as you can ssh in):

[fglrx:firegl_lock_free] *ERROR* lock was not held by 2! (*lock=0x80000001)


Just wondering if anyone running fglrx with a dual head setup is still seeing this problem.  I do have fglrx listed as a DISABLED_MODULES in /etc/default/linux-restricted-modules-common.

---

### Post by higuita on 2008-06-04
This problem have a open bug in the unofficial ati bugzilla:

[http://ati.cchtml.com/show_bug.cgi?id=1041](http://ati.cchtml.com/show_bug.cgi?id=1041)

seems that 8.5 should have fix this problem, at least part of it, the "[fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!" part

---

