---
title: "Increase resolution beyond 1024x768?"
date: 2007-02-06
forum: Desktop Environments
---

### Post by Fourzer0 on 2007-02-06
Howdy!! 

I've been using Windows for quite some time. My first distro was Knoppix STD to test my network for security flaws.. but then I started using Knoppix more and more, until I stopped using windows so I decided to go for a 'real' distro - chose Ubuntu after using Sabayon, Mandriva, Suse. 

Ubuntu is very very perfect for what I need - except I'm using a Radeon X800 graphics card and Ubuntu is only setting my resolution to a maximum of 1024x768 px.. on Windows (I know, comparing Apples to Ant poo) it allowed me to kick my resolution a lot higher than 1024x768... also, Sabayon allowed me to go a lot higher as well!  

Any ideas? I need a bigger resolution because everything looks really big, and I feel squished in my desktop! :|

Mitch

---

### Post by Shay Stephens on 2007-02-07
If the computer does not give you the option of choosing the highest resolution for your monitor, do this in the terminal:

```
lspci
```


That gives a list of the devices installed into the pci bus. Your video card should be among them. Just note which one it is so you can select it in the next step.

again in the terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That will ask you to choose the graphics card manufacturer. I have an nvidia card, so I selected the "nv" entry. Then it asks you to choose the resolutions the card can support. Use the cursor keys to highlight resolution and hit the space bar to check it. I have an lcd monitor, so I just selected the native resolution (1280x1024). When you are done, restart the session by doing a ctrl+alt+backspace or just reboot.

---

### Post by Fourzer0 on 2007-02-07
You are a gentleman and a scholar!  Thank you for your time.

Only problem is, that when I type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It asks for my password [once out of the 6 times I´ve tried this]  but then I type in my password, it presents me with:

```
mitch@FOXTROT:~$
```

Obviously asking for a new command. I searched Google for that command, and it seems it&#347; the correct one to use and not a typo but.. hmm..

I`m using the correct terminal program - so I´m not sure what the issue is.

[edit] I´ve tried many different combinations of the same dpkg command, to no avail... hmm [/edit]

Any ideas?

Mitch

---

### Post by aberry5555 on 2007-02-07
This just means that the command has gone through OK. if you go in to the settings for your screen hopefully it will let you choose a higher resolution now, if not, however, post-up your xorg.conf file and I can show you which bits need editing to create a higher resolution. Also do you use the bog-standard ATI or radeon drivers or have you installed the hardware-accelerated ones?

---

### Post by Shay Stephens on 2007-02-07
> **Fourzer0 said:**
> You are a gentleman and a scholar!  Thank you for your time.

Only problem is, that when I type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It asks for my password [once out of the 6 times I´ve tried this]  but then I type in my password, it presents me with:
That is as it should be, sudo asks for the password once and then remembers it for a few minutes afterward for your computing convenience :-)

> ```
mitch@FOXTROT:~$
```

Obviously asking for a new command. I searched Google for that command, and it seems it&#347; the correct one to use and not a typo but.. hmm..
That is odd.  My guess is that the command is erroring out for some reason and can't run, thus dumping you back into the terminal command prompt.  I don't know what to do about fixing that.

> I`m using the correct terminal program - so I´m not sure what the issue is.

[edit] I´ve tried many different combinations of the same dpkg command, to no avail... hmm [/edit]

Any ideas?

Mitch
As mention, your other option is to edit the xorg.conf file directly.  But this may not work if the root of the problem is trouble with the video card.  I edit the xorg.conf file this way:
```
gksudo gedit /etc/X11/xorg.conf
```

gksudo is a graphical version of sudo for running gui programs like gedit.

Once the file is open, look for the resolution entries toward the bottom of the file.  It will look something like:
> 
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection

Just add the resolution you want to the list.  I have a 1280x1024 LCD, so mine would look like this (additions in red):

> 	SubSection "Display"
		Depth		16
		Modes		[COLOR="Red"]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		[COLOR="Red"]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection

Save and close the file, then restart gnome or reboot the computer.

---

### Post by Fourzer0 on 2007-02-08
Shay,

I thank you for your time and effort regarding this issue - you have solved it for me! It wouldn´t allow me to edit that xorg file through the terminal, so I found it myself through the filesystem and edited it that way.

Very well done my friend! Take care.

Mitch

---

### Post by jpangamarca on 2007-06-15
Hi. I can't increase the screen resolution beyond 1024x768. I've tried everything, even the suggestions posted here, but it just seems impossible. The resolution I want (1152x864) is listed in my xorg.conf file (see below) but Ubuntu won't let me select it. What confuses me more is that the resolutions listed in my xorg.conf file don't match the ones that the Screen Resolution Preferences dialog shows (System Menu > Preferences > Screen resolution) :

xorg.conf : Depth 24 (default): Resolutions: "1152x864" "1024x768" "1000x750" "800x600" "720x400" "640x480"
Screen resolution preferences: "1024x768" "800x600" "640x480" ***"832x624"*** (where did this last one come from????)

I even tried to install the nVidia drivers (my card is a NVIDIA GeForce MX440) but the X system crashes awfully everytime I do. Can anyone help me out? It really sucks having just a 1024x768 resolution, everything looks giant... I should add, I can use a 1152*864 resolution under Windows.

================================================

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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 440]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	HorizSync	30.0 - 55.0
	VertRefresh	50.0 - 120.0
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 440]"
	Monitor		"SyncMaster"
	DefaultDepth	24	
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "1000x750" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


================================================

Thank you very much.

---

### Post by jpangamarca on 2007-06-15
I should add, I can use a 1152*864 resolution under Windows.

---

### Post by abc123456 on 2007-06-16
Try changing DefaultDepth 24 to DefaultDepth 16.  That has worked at higher resilotions  for me.  I use :
 modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@75" 246.59 1920 2064 2272 2624 1200 1201 1204 1253 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
  modeline  "2560x1600@60" 348.16 2560 2752 3032 3504 1600 1601 1604 1656 -hsync +vsync
  
:popcorn:

---

### Post by jpangamarca on 2007-06-17
Oops, DefaultDepth 16 didn't work either, I'm still getting 1152x768@55Hz, not 1152x864@60Hz... Any other suggestion? Thanks.

P.S. What do those modeline values mean?

---

