---
title: "Dual Head screen resolution settings problem"
date: 2005-12-20
forum: Desktop Environments
---

### Post by TomiP on 2005-12-20
I have gotten a dual head setup working but there are few annoying quirks. The most important one is that screen resolutions are not saved correctly when I quit KDE. I set the resolution of my main screen 1600x1200 from the kcontrol and it works fine but after reboot it is 1024x768 - the resolution the second screen had. Meanwhile the resolution of the second screen has changed to 1280x1024. The windows are also slightly different depending on whether they are restored from the previous session or new windows. Konsole for example has slightly bigger fonts and screen borders if I open a new instance compared to Konsole restored from a previous session. And yes, both Konsole instances have same font settings, I checked. Also if I use keyboard shortcuts to go left,right,up or down to another desktop it jumps all over the place in the second screen and imwheel does not work in the second screen - but that is minor. Mainly I would like to get kde save my screen resolutions correctly. Any ideas? I am using KDE 3.5, KDM and Radeon 9000 Pro. I show my xorg.conf also in case it is helpful although the dual head setup as such works fine.

```

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option	    	"ZAxisMapping" "4 5"
	Option	    	"Buttons" "7"
	Option	    	"Resolution" "800"

EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9000 Pro (RV250 If) 0"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9000 Pro (RV250 If) 1"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"

  # 1600x1200 @ 95.00 Hz (GTF) hsync: 120.37 kHz; pclk: 265.77 MHz
  Modeline "1600x1200_95.00"  265.77  1600 1728 1904 2208  1200 1201 1204 1267  -HSync +Vsync

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-150
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9000 Pro (RV250 If) 0"
	Monitor		"SyncMaster"
	DefaultDepth	24
        SubSection "Display"
                Depth           1
                Modes           "2048x1536" "1800x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "2048x1536" "1800x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "2048x1536" "1800x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "2048x1536" "1800x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "2048x1536" "1800x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "2048x1536" "1800x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"ATI Technologies, Inc. Radeon 9000 Pro (RV250 If) 1"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier		"Default Layout"
	Screen		0	"Default Screen"
	Screen		1	"Second Screen" LeftOf "Default Screen"
	InputDevice		"Generic Keyboard"
	InputDevice		"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by localzuk on 2005-12-20
For the first part of your problem my gut feeling would be to remove "1280x1024" from the display subsections of screen 2 and also remove the "2048x1536" "1800x1440" settings from the first screen in your xorg.conf file.

---

### Post by TomiP on 2005-12-20
[QUOTE=localzuk]For the first part of your problem my gut feeling would be to remove "1280x1024" from the display subsections of screen 2 and also remove the "2048x1536" "1800x1440" settings from the first screen in your xorg.conf file.[/QUOTE]

Tried that. That worked with the secondary screen but not with the main screen. I finally got both of them working by removing all settings but 1600x1200 from the first screen in xorg.conf AND unchecking "Apply settings on KDE startup" box in Display section of kcontrol. Well, kind of. I get weird graphical errors on bottom and right side of the screen when I restart which go away by moving the mouse. The screen is not centered correctly at start and by moving the mouse I get it centered and to work as normal. Also I am not able to restart X without getting more serious weird graphics errors, only reboot will do.

Restored and new windows are now the same size, but there are numerous examples of other flaky behaviour, as if KDE has trouble keeping settings of the different screens apart. I can live with that until march of progress fixes things I guess, but I still hope I could get my imwheel working for both screens. I can get it to work if I start it from the command line for the second screen. Where could I put the start command so that it starts automatically for the second screen?

---

