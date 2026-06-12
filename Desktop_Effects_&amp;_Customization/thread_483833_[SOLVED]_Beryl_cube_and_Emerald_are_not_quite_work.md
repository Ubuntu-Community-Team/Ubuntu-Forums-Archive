---
title: "[SOLVED] Beryl cube and Emerald are not quite working right"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by mahasmb on 2007-06-25
I've looked through the Ubuntu forums and the Beryl Project forums but have yet to find anyone with my problems let alone a solution.

Beryl works somewhat but...

#1: I only see four faces when the cube rotates (One by one). I do not see the top or bottom face of the cube. I can not zoom in or out to see the WHOLE cube. I've gone into the Beryl Settings Manager > click on General Options > the Main tab and changed "Horizontal Virtual Size" to 6 as suggested somewhere else for someone whose cube wasn't working at all, but that doesn't seem to help.
>>[IMG]http://img.photobucket.com/albums/v185/SakuraFanelia/Cube.png[/IMG]

*Edit: Now I feel really bad. After two days of not getting #1 to work, I just figured out minutes after posting this that all I have to do is press Ctrl+Alt+hold-and-drag mouse to see the whole cube. I, however, would still like to know if how I can zoom in our out to see the cube at different sizes. Also, I have downloaded the gnome-compiz-manager from Synaptic. 
* I still have an issue with #2!

#2: I can not see the title bar (Including the minimize, maximize and close buttons) of all my windows when I am using Emerald. >>[IMG]http://img.photobucket.com/albums/v185/SakuraFanelia/ScreenshotwithEmerald.png[/IMG]

 However when I'm using Heliodor (GNOME/Metacity Window Decorator, or GTK Window Decorator, the title bars show up fine. >>[IMG]http://img.photobucket.com/albums/v185/SakuraFanelia/ScreenshotMonJune252007.png[/IMG]

_My system:_
- Feisty
- Radeon ATI Xpress 200m
- 512 DDR2 MB
- 1.46 Ghz Intel Celeron M

---

### Post by mahasmb on 2007-06-25
I followed this advice for my problem #2 to no avail:

> **jacquesvn said:**
> Not sure if you have double checked this but found that this was my problem:

Firstly the  [Option         "AddARGBGLXVisuals" "True"]  Originally fixed my problem - so make sure you have this under the device entry.

Next in changing my conf file to get my tv out to work I used a DefaultDepth  of 16 with the corresponding entry. After this no more title bar - changing it to 24 and updating the relevant entry to 24 fixed the problem. Not sure why the difference between 16 and 24 but there you have it.

So in a nutshell:

Ensure Option         "AddARGBGLXVisuals" "True" exists in Device
Ensure Depth Value of 24 e.g. 
Section "Screen"
.... 
    DefaultDepth    24 
    SubSection     "Display"
        Depth      24 
        Modes      "1024x768"
    EndSubSection
....
EndSection

Hope this worked - else post your conf file and lets have a look at it.

Cheers :)


Here's my Xorg.conf file
```
# bare-bones XFree86 config to start the server in probe-only mode
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	RgbPath		"/etc/X11/rgb.txt"
EndSection
Section "ServerFlags"
	Option "AllowMouseOpenFail"
EndSection
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
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
	Identifier	"Generic Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
EndSection
Section "Device"
	Identifier	"Generic Device"
	Driver		"::DRIVER::"
EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection
Section "Screen"
	Option "AddARGBGLXVisuals" "True"
	Identifier	"Default Screen"
	Device		"Generic Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
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
	InputDevice	"Generic Mouse"
EndSection
```

---

### Post by mikec13 on 2007-06-25
Try moving this: Option "AddARGBGLXVisuals" "True" from the Screen section to the Device section.

---

### Post by mahasmb on 2007-06-25
```
# bare-bones XFree86 config to start the server in probe-only mode
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	RgbPath		"/etc/X11/rgb.txt"
EndSection
Section "ServerFlags"
	Option "AllowMouseOpenFail"
EndSection
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
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
	Identifier	"Generic Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
EndSection
Section "Device"
	Identifier	"Generic Device"
	Driver		"::DRIVER::"
	Option "AddARGBGLXVisuals" "True"
EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection
Section "Screen"	
	Identifier	"Default Screen"
	Device		"Generic Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
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
	InputDevice	"Generic Mouse"
EndSection
```

Here's my file again and the title bars are still invisible.

---

### Post by mikec13 on 2007-06-25
Have you tried running "emerald --replace &" in the terminal to reload it?  Just throwing out a couple things that worked for me...

---

### Post by trofim on 2007-06-25
Take file from this post: [http://ubuntuforums.org/showthread.php?t=437802](http://ubuntuforums.org/showthread.php?t=437802)

Don't forget to make it executable chmod a+x.

Cheers,

---

### Post by mahasmb on 2007-06-26
Thanks trofim!

That worked!

Just one question though ... I'm pretty new to Linux and I was wondering if there was a faster way to open and extract the file to a folder that requires administrative rights than the way I did it. I basically just moved it one by one from folder to folder with the terminal.

---

### Post by ivesjd on 2007-06-26
you could do it like this EX: mv text.txt /usr/local/bin/folder/newfolder/text.txt

---

### Post by nowshining on 2007-07-27
hey do zoom in and out do this set the zoom in and out keys to

zoom in - ctrl + alt + up
Zoom out - ctrl + alt + down

u know the up and down arrow keys on the keyboard, that is what helped me on that one.. :) but the top bottom thing I also had..hope this helps..

---

