---
title: "Look at this Screen Shot Please Help Me!"
date: 2006-04-15
forum: Desktop Environments
---

### Post by lonelypauly on 2006-04-15
This is the only thing keeping me from abandoning Windows completely...

 I have 2 monitors running from a dual head Nvidia GeForce 6800 Ultra...I can run both monitors in SPAN MODE perfectly in Windows. with Ubuntu 5.10 however, I am only able to use 1 monitor.  

Funny thing is, as Ubuntu is booting up, both monitors work fine, but as soon as the login prompt appears, I get the following message on my 2nd monitor:

[IMG]http://i6.photobucket.com/albums/y215/lonelypauly/img_0618.jpg[/IMG]


Any Ideas?

---

### Post by CompShrink on 2006-04-15
Please post the contents of your /etc/X11/xorg.conf file.

It looks like you just have the refresh rate off. Are both monitors the same, or are they different?

---

### Post by lonelypauly on 2006-04-16
both monitors are exactly the same.  however, i should note that one of them was repaired last year when the picture gave out altogether.  would this have anything to do with it?  how would i adjust the refresh rates?  thank you for the response by the way.

---

### Post by Ramses de Norre on 2006-04-16
Boot into recovery mode and do
```
cd /etc/X11 && cp xorg.conf xorg.conf.bak && vi xorg.conf
```
Scroll down to the monitor sections, press i to ge into insert mode, and add following lines with the correct values (maybe the ones shown on the error screen but I'm not sure, check monitor manual)
```
    HorizSync     31-101
    VertRefresh    60-160
```
Then press esc, shift+q, type wq! and press enter
Then do ```
init 6
``` to reboot.

---

### Post by CompShrink on 2006-04-16
Um, vi is scary... honestly... although all console editors are to some extent. But notice he said one monitor works just fine. So open a terminal and put in:

cd /etc/X11 && sudo cp xorg.conf xorg.conf.bak && sudo gedit xorg.conf

Now, find the working monitor. I would assume it is the one with the lower values for HorizSync and VertRefresh. Then copy those values and put them in the section for the other monitor.

Reboot, and see if it works.

If it still doesn't work, I would try completely copying the one monitor's description (the one that had lower values in the first place) and just changing the Identifier setting, and restart and see.

Tell us if it works or not.

---

### Post by lonelypauly on 2006-04-16
Please take a look at my xorg.conf file...i don't think it's setup for 2 monitors to begin with...

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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Driver		"nv"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"GatewayVX112"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Monitor		"GatewayVX112"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Ramses de Norre on 2006-04-16
This changes the issue.. I didn't notice one did work.
But you'll need to edit your xorg.conf in order to get two monitors working, search the forums for nvidia twinview.
Maybe the issue is caused by the second screen not being configured (though normally it should just blank..).

---

### Post by 146lily on 2006-04-16
Dapper may sort it, I think it can walk on water.

---

### Post by CompShrink on 2006-04-17
No, you don't have the second monitor set up at all yet. They both connect to 1 video card, right?

If so, I would read through the first two links in this thread:

[http://ubuntuforums.org/showthread.php?t=85769&highlight=twinview+howto](http://ubuntuforums.org/showthread.php?t=85769&highlight=twinview+howto)

Hope that helps.

---

