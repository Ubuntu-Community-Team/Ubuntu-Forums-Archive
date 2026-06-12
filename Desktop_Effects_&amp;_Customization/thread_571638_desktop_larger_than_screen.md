---
title: "desktop larger than screen"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by dolittle on 2007-10-09
Hi All,
      I just did a distro upgrade from 7.04 to 7.10. Everything went smoothly and I had Twinview working in about one minute. Thanks. My problem is that the desktop is larger than the display(s). I have two identical 17" LCDs at native 1280x1024 resolution and 60 Hz refresh. At boot I see wallpaper :confused: If I move my cursor to any edge the desktop scrolls. To find and launch Firefox, as an example, I must move the cursor to the top to find the toolbar then left to find menus and icons. Any help appreciated. I am including my xorg.conf in case that is helpful.

Thanks in advance
Allan

........
Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"BenQ"
	Modelname	"BenQ FP731"
	Horizsync	31.5-83.0
	Vertrefresh	60.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
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
	Device		"nVidia Corporation NV43 [GeForce 6600]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1792x1344@60"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" rightof "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1792x1344@60"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"BenQ"
	Modelname	"BenQ FP731"
	Horizsync	31.5-83.0
	Vertrefresh	60.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
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
Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection

---

### Post by amadeus266 on 2007-10-09
I'm no expert by any means but this sounds as if your using a virtual desktop size that is larger than your actual display size.

This may be an indication of the problem
```
Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation NV43 [GeForce 6600]"
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
[COLOR="Red"]Virtual 1792 1344[/COLOR]
Modes "1280x1024@60" "1280x960@75" "1280x960@60" "1400x1050@60" "1280x1024@75" "1400x1050@75" "1152x864@75" "1600x1200@65" "1024x768@60" "1600x1200@60" "1024x768@70" "1792x1344@60" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "640x480@75" "640x480@72" "640x480@60"
EndSubSection
EndSection
```

Some systems/monitors allow this type of setup and others don't.

If anyone is more versed on this than I am PLEASE correct me. I would hate to steer this guy in the wrong direction.

---

### Post by oswallt on 2007-10-09
The same thing is happening to me.  Compiz installed the nvidia driver and now everytime I restart my computer the desktop is bigger than my screen.  I don't see anything for virtual desktops in the Compiz Manager, in Appearance, or the Screens and Graphics Preferences.  Is this something I need to edit my xorg.conf for?

---

### Post by Forlong on 2007-10-09
> **amadeus266 said:**
> If anyone is more versed on this than I am PLEASE correct me. I would hate to steer this guy in the wrong direction.
No, that's absolutely correct. The right setting would be
```
Virtual 2560 1024
```

@oswallt: post your xorg.conf - and please use the forum's CODE tag (# button)

---

### Post by oswallt on 2007-10-09
I'm comfortable with editing my xorg.conf, I just don't know if there's a spiffy new GUI for editing the virtual size somewhere I haven't seen.  I don't remember ever seeing the Virtual section before, though, so I'm not sure if I should just delete it or change it to the default I want.  I should mention that I'm using just one monitor, not two.

Here's my xorg.conf:
```

Section "Files"
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
	Identifier	"nVidia Corporation NV35 [GeForce FX 5900]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"BenQ"
	Modelname	"BenQ FP731"
	Horizsync	31.5-83.0
	Vertrefresh	60.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
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
	Device		"nVidia Corporation NV35 [GeForce FX 5900]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1792x1344@60"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #          
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #          
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #          
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by smartboyathome on 2007-10-09
The virtual section is right under the section with all those desktop sizes.

---

### Post by Forlong on 2007-10-10
@oswallt: if you are using only one monitor it should be safe to remove the option entirely.

But you can change it as well to:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV35 [GeForce FX 5900]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
[COLOR="Red"]		Virtual	1280	1024[/COLOR]
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1792x1344@60"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
```

---

### Post by dolittle on 2007-10-10
Thanks amadeus266 and Forlong. The correct setting on my machine was 'Virtual 1280 1024' 
Now why won't my terminal launch.....I know ...one thread at a time.:guitar:

Allan

EDIT    not working perfectly after all

---

### Post by Ubuntized! on 2007-10-10
how did you try to lauch your terminal?!?? I mean what did u clicked?!

---

### Post by oswallt on 2007-10-10
Thanks Forlong!  I'm going to go ahead and delete it, I can't think of anything I would need it for.

---

### Post by dolittle on 2007-10-11
I'm back,

     Unfortunately changing the 'virtual' settings is not enough. My desktop is still about 100 pixels (a guess) larger than the screen(s).:confused:

     Ubinized..I tried to launch the terminal from the menu system: Applications-Accessories-Terminal. The only result was an "hour glass" for 90 seconds then nothing...no error report. I did check to see that it was installed so that's not the problem.
     
Thanks for your interest,
Allan

---

### Post by Forlong on 2007-10-11
I'd recommend resetting your xorg conf.
Do a backup first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then:
```
sudo dpkg-reconfigure xserver-xorg
```
And afterwrds:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Reboot and see if everything works for you - then you can go ahead configuring your dualhead setup.

---

### Post by dolittle on 2007-10-11
Again,

     Forlong: I tried everything you suggested. Since I still can't get the terminal to launch, I used Ctrl-Alt-F1 and worked from there. The initial results were good; I had one screen working as advertised. Then I configured for a second monitor and was back to my original problem. Also the same 'virtual' with odd parameters comes up.
     As an aside I'm having problems with attachments and I'm getting the feeling that I will have to produce logs configs and results of diagnostics. I will RTFM for that so that I can provide details.:)

Thank you all for your attention to this problem,

Allan

---

### Post by Forlong on 2007-10-11
Alright, so we narrowed it down to the part where you set up your second monitor. How do you do that? Via "Screens and Graphics"?

---

### Post by dolittle on 2007-10-11
wow that was fast!

Yes is setup via the 'wizard' with a default monitor 1280x1024 60Hz and the second 'right of default with same settings; both monitors are identical.

Allan

---

### Post by Forlong on 2007-10-11
OK, unfortunately I don't have two monitors, so I can't test it myself but it looks like there's a bug in the application then.

I know there are ways to achieve this manually but again, I don't have any experience with that. I recommend doing the resetting thing again and then go here: [https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

Hope this helps.

---

### Post by dolittle on 2007-10-11
Forlong...thanks. I will do more research.

One note.....Option 'Twinview' does not appear in the xorg.conf but in the syntax of xorg.conf there are many ways to do the same thing. Never-the-less I'm used to seeing this
option along with 'right of'

I think I'll take a break fro breaking my computer:lolflag:

Allan

---

### Post by Ubuntized! on 2007-10-12
Hi

Did you try Alt+F3!?(Dunno if this is also ur shortcut! Anyway go to system-prefernces-keyboard shortcuts..) Try and install 'Konsole'! maybe u can manage to find out what's wrong!
Just an idea!
Surely u r more experienced than I am!!!

---

