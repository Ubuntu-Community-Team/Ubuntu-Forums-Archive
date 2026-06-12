---
title: "why does  compiz  not work"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by dellboy on 2007-12-04
ok i think i have instilled  compiz on my ubuntu as when i go to system perfections then i can Click advance desktop effects setting  but when i Click on say   desktop cube or watter effect 

northing happens how comes thank you for you help

---

### Post by rich.bradshaw on 2007-12-04
If you activate the cube and rotate cube plugins, then hold control and alt and move mouse, what happens?

---

### Post by Fanin on 2007-12-04
try restarting your pc?

---

### Post by dellboy on 2007-12-04
try both still dose not work

---

### Post by Crumpets and Jam on 2007-12-04
Do you have the latest drivers for your graphics card installed?

---

### Post by dellboy on 2007-12-04
not sure how do i check i am new to Linux lol i:)

---

### Post by SpacePilot on 2007-12-04
You need direct rendering. To check if it works you type:

glxinfo | grep direct


I have direct rendering and I only get a two sided cube, but all the other disturbing effects work. Trust me, if you are working on this computer you will turn most of them off :D

---

### Post by dellboy on 2007-12-04
ok it comes up with 
direct rendering: Yes

that help anything

---

### Post by onion221 on 2007-12-04
Super+R and move your mouse around or water effect.

---

### Post by dellboy on 2007-12-05
> **onion221 said:**
> Super+R and move your mouse around or water effect.

Super that is that  ????:confused:

---

### Post by dellboy on 2007-12-20
still not got this working anyone now why

---

### Post by dr.phees on 2007-12-20
I have the same problem, I can't get that cube-effect working. When I hold [Alt]+[STRG], the desktop shrinks a bit, being reflected off a "plane" beneath it, just as it should, but I can't turn it.
The cause might be, that I can't set the number of desktops to more than just one. In xfce I use 3, but with compiz I can't set more than one. The xfce pager is reduced to one either, when compiz is started. Strange.
I am this (||) short to trying gnome, but for now I like xfce better. And it shouldn't have to do with that, I guess...

All the transparency stuff works, direct rendering is activated, too, games, google earth etc. work flawless.

---

### Post by Espreon on 2007-12-20
> **dellboy said:**
> Super that is that  ????:confused:

Super = The Window$ key

---

### Post by dellboy on 2007-12-20
i can not seem to get anything to work at all ???:confused:

---

### Post by Espreon on 2007-12-20
OK,

1. Which version of Ubuntu are ye running

2. Are ye runnin Compiz or Compiz-Fusion (the one that ships with Gutsy)

3. Enter this in the terminal and post the outputs:

```
compiz
```

---

### Post by dellboy on 2007-12-20
1. ubuntu 7.10  
2 dont now i add my to my computer 
3.
compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2972' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


Dose this help

---

### Post by Espreon on 2007-12-20
OK now:

1. What brand is your graphics card

2. Which driver are you using? vesa, fglrx (a.k.a The "Restricted Driver"), etc.

3. Try installing XGL:

```
sudo apt-get install xserver-xgl
```

After it is done installing XGL:

Also another problem  is that your card is blacklisted so enter this in the terminal as well:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Then hit CTRL-ALT-Backspace and log back in

---

### Post by dellboy on 2007-12-20
1. i810 intel intergeted Gaphics Chipset (intel 965) i think
 installing XGL: still dose not work 
2. not sure ?
3.

```
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following extra packages will be installed: 
  libglitz-glx1 libglitz1 
The following NEW packages will be installed 
  libglitz-glx1 libglitz1 xserver-xgl 
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded. 
Need to get 1843kB of archives. 
After unpacking 4854kB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get: 1 http://gb.archive.ubuntu.com gutsy/main libglitz1 0.5.6-1 [76.6kB] 
Get: 2 http://gb.archive.ubuntu.com gutsy/main libglitz-glx1 0.5.6-1 [29.6kB] 
Get: 3 http://gb.archive.ubuntu.com gutsy/universe xserver-xgl 1:1.1.99.1~git20070727-0ubuntu3 [1737kB] 
Fetched 1843kB in 3s (613kB/s)        
Selecting previously deselected package libglitz1. 
(Reading database ...   
```

nstalling XGL: still dose not work

---

### Post by Espreon on 2007-12-20
Do this:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

After that hit CTRL-ALT-Backspace, log back in.

If Compiz still does not work give me the output of:

```

compiz

```

---

### Post by dellboy on 2007-12-21
ok the Frist code did not do anything 

so here is the out of the other 

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by Espreon on 2007-12-21
OK, first of all the 1st one did do something, your card is no longer blacklisted, please post the contents of your xorg.conf file by doing the following:

```

gedit /etc/X11/xorg.conf

```

then copy everything from that file into a post.

---

### Post by dellboy on 2007-12-21
ok how comes my card was black listed 


```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
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
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"Intel Corporation 82946GZ/GL Integrated Graphics Controller"
	Boardname	"i810"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Hanns.G HW17"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
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
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82946GZ/GL Integrated Graphics Controller"
	Monitor		"Hanns.G HW17"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "ServerFlags"
EndSection
```

---

