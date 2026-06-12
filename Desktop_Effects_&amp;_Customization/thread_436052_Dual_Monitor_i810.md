---
title: "Dual Monitor i810"
date: 2007-05-07
forum: Desktop Effects &amp; Customization
---

### Post by Seeker84 on 2007-05-07
I've been banging my head against the desk when I try to figure this dual-monitor thing out. I am currently trying to get my Dell Inspiron 700m Laptop to use It's screen and an external LCD. I have followed many threads and have came up with nothing. Please look over my xorg file so I don't have to keep banging my head on the desk.

Some things to keep in mind, I'm working off a Intel 82852/855gm integrated Graphics card. I have updated to the best of my ability any packages from synaptic, driver is i810.

xorg.cof:
```


Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	#Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Identifier	"Main Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	#Option		"DisplayInfo" "FALSE"
	Screen		0
	#Option		"VBERestore" "false"
	#Option		"DDC" "true"
	#Option		"Monitor Layout" "LFP, LFP2"
	#Option		"Monitor Layout" "CRT, LFP2"
	Option		"Monitor Layout" "CRT, LFP"
EndSection

Section "Device"
	#Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Identifier	"External Device"
	Driver		"i810"
	BusID		"PCI:0:2:1"
	#Option		"DisplayInfo" "FALSE"
	Screen		1
	#Option		"VBERestore" "false"
	#Option		"DDC" "true"
	#Option		"Monitor Layout" "LFP, LFP2"
	#Option		"Monitor Layout" "CRT, LFP2"
	#Option		"Monitor Layout" "CRT, LFP"
	
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	#Option		"Monitor Layout" "LFP, LFP2"
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"Main Device"
	Monitor		"Main Monitor"
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

Section "Screen"
	Identifier	"External Screen"
	Device		"External Device"
	Monitor		"External Monitor"
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
	Screen		"Laptop Screen"
	Screen		"External Screen" RightOf "Laptop Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

#Section "ServerFlags"
#	Option		"Xinerama"
#EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by hikentao on 2007-05-18
Yeah...I've been trying to find an effective configuration for an intel i910 on a Toshiba laptop.  My xorg configuration doesn't look that much different, so I won't post.  I've also tried a lot of solutions from various posts.  

Anyone's help is much appreciated.

---

### Post by Seeker84 on 2007-05-24
So I was able to get the External monitor to work, not it's just solving beryl issues that I will make a new thread on.

but at this post [http://ubuntuforums.org/showthread.php?t=301951&page=19](http://ubuntuforums.org/showthread.php?t=301951&page=19) reply #182 was my road to victory.  All I had to do was change "CRT, LFP" to "CRT,LFP" and I got both monitors to work.

There are lots of commented out line in this I'll post a cleaner version later but here are the important bits for my xorg.conf:
```

Section "Device"
	#Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Identifier	"Main Device"
	Driver		"i810"
	#Option		"DisplayInfo" "FALSE"
	#Option		"VBERestore" "false"
	#Option		"DDC" "true"
	#Option		"Monitor Layout" "LFP, LFP2"
	#Option		"Monitor Layout" "CRT, LFP2"
	Option		"Monitor Layout" "CRT,LFP"
	Option 		"DRI" "false"
	#Option		"DevicePresence" "true
	Screen		0
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	#Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Identifier	"External Device"
	Driver		"i810"
	#Option		"DisplayInfo" "FALSE"
	#Option		"VBERestore" "false"
	#Option		"DDC" "true"
	#Option		"Monitor Layout" "LFP, LFP2"
	#Option		"Monitor Layout" "CRT, LFP2"
	Option		"Monitor Layout" "CRT,LFP"
	Option 		"DRI" "true"
	#Option		"DevicePresence" "true
	#VideoRam	131072
	Screen		1
	BusID		"PCI:0:2:0"
	
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
	HorizSync	30-60
	VertRefresh	50-100
	#Option		"Monitor Layout" "LFP, LFP2"
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	Option		"DPMS"
	HorizSync	28-82
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"Main Device"
	Monitor		"Main Monitor"
	DefaultDepth	16
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

Section "Screen"
	Identifier	"External Screen"
	Device		"External Device"
	Monitor		"External Monitor"
	DefaultDepth	16
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
	Screen		0 "Laptop Screen"
	Screen		1 "External Screen" RightOf "Laptop Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "on"
	Option		"Clone" "off"
EndSection

```

I got the HS and VR for each monitor from their manuals and/or google searches

---

### Post by Skipster on 2007-06-01
This worked great on my Thinkpad X40!

Thanks a bunch !

Skip

---

### Post by jamesrl on 2007-08-07
The above method didn't work for my setup (Xinerama also didn't work for me), but the method I describe below did.
My Setup: Feisty 7.04 on a laptop with native 1680x1050 resolution and Intel 945GMA (i810) [Dell Inspiron e1505; though bought prior to Dell selling ubuntu], hooked up (through VGA cable) to an external 1680x1050 flat screen display.  

I kept trying all these methods but couldn't get anything to work and kept killing x and going back and forth back and forth with restarting X and was very time consuming.

What did work for me: the updated version of xserver-xorg, and intel-video (Gutsy's current version) with very simple edit to xorg.conf and 1 liner command from the terminal.  I found the method from _[this howto on the xorg mailing list written in June 2007]("http://lists.freedesktop.org/archives/xorg/2007-June/025990.html")_.

Step 1:
Get Gutsy version of xserver-xorg, xserver-xorg-video-intel, xrandr.  [How to do this from feisty is explained below].  One method would be to just install gutsy (which is what i ended up eventually doing).

Step 2:
Find your favorite text editor, open up /etc/X11/xorg.conf as root and add a "Virtual" line to every display mode listed in screen.  For my case, I was running two monitors at 1680x1050 running next to each other, so added the line "Virtual 3360 1050" as shown below
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel i945GMA"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050"
                Virtual         3360 1050
        EndSubSection
...

```
Note, you can edit an unmodified version of /etc/X11/xorg.conf that works solely for one display.  [That is you do not need to have two Devices and Monitors and Screens or a modified ServerLayout.  In fact if you do it may cause problems].  If you want to generate a new generic one, just run "sudo dpkg-reconfigure xserver-xorg" or just copy your backup xserver.xorg from before you edited it.

Step 3: Restart X with your new xorg.conf saved, by either Ctrl-Alt-Backspace or reboot the computer.

Step 4: hook up the external monitor, go to a terminal and type
```

xrandr --output VGA --left-of LVDS --auto

```
and it should work!  Note, if you want the monitors on the other side you can change --left-of to --right-of; also you could have above/below (note need different Virtual line then; doubling the second number).  Look at the update xrandr man page.

Other things you can do.  You can also switch to having a cloned display with 
```

xrandr --output VGA --same-as LVDS

```
or turn it off by unplugging the monitor and typing,
```

xrandr --output VGA --auto

```

OK, so I glossed over one somewhat complicated step of updating the right files from the Gutsy depository to have them run in feisty.  What i did was add the following two lines to /etc/apt/sources.list:
```

deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy main restricted universe multiverse

```
then ran (ignoring all the gutsy updates package manager says there are):
```

sudo apt-get update
sudo aptitude install xserver-xorg-video-intel xserver-xorg libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa mesa-utils mesa libdrm2 libxdamage libgl1-mesa libglu1-mesa mesa-utils x11proto-print xorg-server xnest xprint xserver-xorg-video-intel beryl beryl-manager xrandr

```
Then I commented out those two lines and ran sudo apt-get update again (so I don't have announcements of ~800 updates popping up). 
Note I stole this section from [this post]("http://ubuntuforums.org/showpost.php?p=3106512&postcount=47") with the addition of updating xrandr as well.

Cheers

---

