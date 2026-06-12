---
title: "Getting XLIB errors when trying to install a game."
date: 2006-09-11
forum: Gaming &amp; Leisure
---

### Post by Raavea on 2006-09-11
I'm trying to install a game, and I'm getting this error over and over again;
```
Xlib:  extension "GLX" missing on display ":0.0".
```
I've searched the game's forums, and the ubuntu forums, but nothing new or helpful comes up. I did find a thread that told me to;
```
ln -sf /usr/X11R6/lib/modules/extensions/libglx.{so,a}
```
 But that didn't work;
```
ln: creating symbolic link `/usr/X11R6/lib/modules/extensions/libglx.a' to `/usr/X11R6/lib/modules/extensions/libglx.so': No such file or directory
```
 Which is correct, I did some exploring and there is no such directory. And thus no file. So a double-barelled question here;
 * Firstly, has executing that command borked anything, and if so, how do I undo it?
 * Secondly, how do I fix this?


 Much thanks in advance.
*(PS: It's the only problem I have had in this installation so far that I can't figure out how to fix. I have the correct nVidia drivers installed, I even re-installed them and rebooted, and am still getting the error.)*


 EDIT: The command glxinfo displays the following - not sure if it's a help but the few threads I could find mentioning this error seem to want this to be posted. :)
```
raavea@bernard:~/EternalLands$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
```

 And here's my xorg.conf:
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```


EDIT2: A second re-installation of the nVidia EVERYTHING has resulted in no change. I installed nvidia-controls or somesuch thing too, so I shall be playing about with that to try to figure out if it's a setting that's wrong.

---

### Post by croak77 on 2006-09-12
1. Is that really how your xorg.conf looks? Cuase the way you posted it, the format is way off. Use line wrap or word wrap. If using nano use nano -w /etc/X11/xorg.conf. Things that are supposed to be on their own line are not. Things that are one line are two.

2. You have the nv driver selected not nvidia.

3. I would suggest running fro a terminal;
```
sudo dpkg-reconfigure xserver-xorg
```
It will ask you all kinds of questions about mouse, keyboard, driver (select nvidia not nv), resolution, etc.

---

### Post by Raavea on 2006-09-13
Thanks. However, 'nvidia' was not even listed. The closest was nv. So I selected nv. I had no fricking idea what those questions just asked, so I let it do what it offered. -_-

I've managed to get xorg to print out with better alignment. Edited the first post with the new xorg output.


EDIT: I just uninstalled everything related to nvidia that seemed safe to uninstall again, and then used [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") to re-install it all from scratch. Am about to test if it worked.


EDIT2: Yup, all fixed. In future I won't be lazy and use EasyUbuntu for installing drivers if I re-install Ubuntu. x.x

---

