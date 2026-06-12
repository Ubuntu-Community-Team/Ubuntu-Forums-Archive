---
title: "Title bar missing with Compiz"
date: 2007-10-30
forum: Desktop Environments
---

### Post by wrongOne on 2007-10-30
Hey im running compiz on ubuntu 7.10, on an acer aspire 5600 (945pm express chipset with GMA graphics)

When i go into System->Preferences->Appearance and put effects on custom (so i can control them with compiz's "advanced desktop effects settings", i loose all the title bars on windows. This presents a problem since it renders wobbly windows useless since i cant move them and i cant resize or minimize without moving the mouse to the panel.......anyone know any quick fixes for this or if compiz has a control to hide the title bar of windows?

---

### Post by Thyme on 2007-10-30
Does compiz startup automatically after you login and without problems? Can't you contol Compiz without having to put the effects on custom or must you?

---

### Post by tony11235 on 2007-10-31
I'm having the same problem on my desktop. I have a GeForce4 MX. When i switch to even normal effects, my title bars are missing. Even after I logout or reboot. This is my xorg.conf

> 
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
	Load		"v4l"
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
	Option		"Protocol"	"auto"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"ButtonMapping" "1 2 3 6 7"
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
	Identifier	"nVidia Corporation NV18 [GeForce4 MX - nForce GPU]"
	Boardname	"nv"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Hewlett-Packard"
	Modelname	"HP F1503 Flat Panel Monitor"
	Horizsync	30.0-63.0
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
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"1024x768@60"	"1280x960@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
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

Section "device" # 
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Screen	1
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
Section "Extensions"
	Option		"Composite"	"enable"
EndSection


---

### Post by Thyme on 2007-10-31
if you type in "emerald --replace" then do the titlebars re-appear?

---

### Post by tony11235 on 2007-10-31
But what does emerald have to do with compiz-fusion? I don't have emerald installed. On my laptop I have compiz-fusion effects working without emerald installed and I have my title bars.

---

### Post by kaputme on 2007-11-30
Hey..
i am very new to ubuntu... saw the effets of compiz-fusion...
I have a nvidia geforce4 mx nforce graphics..have the driver installed but not able to enable  desktop effects.. helpppppp..
as i said i am new to linux......so please explain in detail....
Thanx in advance

---

### Post by E21Craze on 2007-12-01
> **Thyme said:**
> if you type in "emerald --replace" then do the titlebars re-appear?

Hi there.

Just noticed this problem and tried "emerald --replace". It brings back the titlebars but as soon as you close the terminal window they disappear... along with the "close-minimize-restore" buttons.

---

### Post by MetCom45 on 2007-12-12
I am having the same problem, With or without Emerald installed. I am using an ATI graphics card as well. 

I would also like to mention i have had the same problem with Beryl on Ubuntu 7.04

I would really like a solution to this problem, it is extremely annoying ;p

---

### Post by MetCom45 on 2007-12-12
Alright i worked with this a bit, and I did something that seemed to have worked for me. 

Open terminal, 

> sudo gedit /etc/X11/xorg.conf

go towards the bottom and look for the lines

"Section "Extensions"
	Option		"Composite"	"0"
EndSection"

where it states "0", change it to "enable"

Like so:
"Section "Extensions"
	Option		"Composite"	"enable"
EndSection"

my title/taskbars and buttons are all working. 

*note i am using an ATI card with FGLRX

I would really appreciate some feedback if this worked for anyone else =D

UPDATE~ i restarted, and tried a few things. worked for a while. then i messed with some plugins, and bam, title bars are missing again :0

---

### Post by Eddy5 on 2007-12-22
I had lost my title bars, and it was all running slowly (Plus FreeGuide wasn't displaying).
I'd noticed that when I hovered over a program in the program bar at the bottom I was getting a preview of the window. Somehow some effects had been enabled, so I went to 
System - Preferences - Appearance
and turned off Visual Effects and everything is running lovely and fast again (No effects of course, but then I don't use them as my laptop is too slow for them).

---

### Post by barrack on 2007-12-22
> **E21Craze said:**
> Hi there.

Just noticed this problem and tried "emerald --replace". It brings back the titlebars but as soon as you close the terminal window they disappear... along with the "close-minimize-restore" buttons.

If you add "emerald --replace" to your start up, then you should be set. The command will be run everytime you log-in. 

To do this go to System > Preferences > Sessions and add the add a new item.

---

### Post by devchang on 2008-01-24
> **barrack said:**
> If you add "emerald --replace" to your start up, then you should be set. The command will be run everytime you log-in. 

To do this go to System > Preferences > Sessions and add the add a new item.

I just tried this and everything works fine now, thank you very much. :-D

---

### Post by LeDechaine on 2008-02-06
> metacity --replace
Worked for me.
Someone somehere in the forum said that this command replaced the theme to the originl ubuntu theme, but this command, for me, just bringed back my menu/status bars.

And for E21Craze, i think that **emerald --replace** should be run via alt+F2, not via the terminal! ;)

Ah! Also, when enabling the "cube", if you don't see the bars, **ctrl+alt+right arrow** or **ctrl+alt+left arrow** wakes them up for me!

---

### Post by poisonblack on 2008-02-07
I got over this problem by following method:
-Open compizconfig-settings-manager.
-Click on Window Decoration and enable it.
-In the Command box, type in emerald
Worked for me.Hopefully will work for you too.!:KS

---

### Post by jhenager on 2008-02-27
> **Eddy5 said:**
> I had lost my title bars, and it was all running slowly (Plus FreeGuide wasn't displaying).
I'd noticed that when I hovered over a program in the program bar at the bottom I was getting a preview of the window. Somehow some effects had been enabled, so I went to 
System - Preferences - Appearance
and turned off Visual Effects and everything is running lovely and fast again (No effects of course, but then I don't use them as my laptop is too slow for them).
Thank you. Your suggestion worked.

---

### Post by optimusmedia on 2008-03-07
> **Thyme said:**
> if you type in "emerald --replace" then do the titlebars re-appear? 

Awesome!  That worked perfectly for me.  Up until this, I've been reloading X.  (Ctrl+Alt+backspace).

---

### Post by angry_johnnie on 2008-03-08
type

emerald --replace & disown

that way, when you close the terminal, emerald will continue to run.

---

### Post by hulio40 on 2008-03-08
try this

open a terminal and type:


sudo nvidia-xconfig --add-argb-glx-visuals


and then restart

---

