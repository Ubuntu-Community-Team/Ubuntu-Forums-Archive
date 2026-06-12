---
title: "Help with Dualscreen/Xinerama"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Ragzouken on 2006-08-17
This, pulled from 'lspci' in terminal, shows my Graphics card, a Radeon 9550 with two outputs.

```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)
```

Below is from my xorg.conf, I have not included the "InputDevice"s in this post.

I've followed some tutorials for Dualscreen/Xinerama to come up with this xorg, but it didn't change anything, it all works the same as when I didn't change it.

```
Section "ServerLayout"
	Identifier     "Multihead"
	Screen		0	"aticonfig-Screen[0]"	0	0
	Screen		0	"aticonfig-Screen[1]"	0	0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	Option	    "Xinerama"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "Monitor"
	Identifier   "SAMTRON"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "CRT-Thing"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI 2"
	Driver      "ati"
	BusID       "PCI:1:0:1"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "ATI 2"
	Monitor    "CRT-Thing"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor    "SAMTRON"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

I asked a friend who is quite knowledgeable on the subject, but he said it should be right, can anyone here say if I'm doing it drastically wrong, or if something else is to blame?

---

### Post by gerbman on 2006-08-17
I am assuming you restarted X with CTRL+ALT+BKSP after making the changes. If you didn't, try it. I have dual-screen working with my Radeon 9500 Pro, and I am not using Xinerama. I have attached my xorg file for reference.

---

### Post by Ragzouken on 2006-08-17
Thanks to your help I managed to get it working, but with some problems:

I can switch the screen numbers around to get my desktop shortcuts to be on the right (not left) screen, but I can't get the log in or taskbar/etc to be on the right (not left) screen.

My xorg is now: (minus irrelevant bits)
```
Section "Device"
	Identifier	"ati-radeon[1]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Device"
	Identifier	"ati-radeon[0]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Monitor[0]-Flat"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	56-75
EndSection

Section "Monitor"
	Identifier	"Monitor[1]-CRT"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"ati-radeon[0]"
	Monitor		"Monitor[0]-Flat"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen[1]"
	Device		"ati-radeon[1]"
	Monitor		"Monitor[1]-CRT"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0  "Screen[0]" 0 0
	Screen		"Screen[1]" RightOf "Screen[0]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option		"Xinerama"
EndSection
```

Also, when not using Xinerama, how can I move a window to the other screen?

---

### Post by gerbman on 2006-08-17
I'm not sure about your first question (getting the login screen to appear on the other monitor), but I can answer your last question: I don't think you can. I have yet to find a way to drag windows from screen to screen without using a third-party app like Xinerama (which I haven't used successfully). Right now I'm just making do, starting applications on the other monitor if I want them there.:confused:

---

### Post by Ragzouken on 2006-08-17
What I mean is, in Xinerama, it's always using the left screen to put the Taskbar/Workspace bar, and the Applications/Places/System/Time-Date on, I can seem to get them on the right screen whatever I do.

---

### Post by b_martinez on 2006-08-17
switch your cables and then edit xorg.conf to show #2 "left of" #1 ??? Of course, all the icons on the left of screen 1 will end up in the middle
of your vision.
Of course, this may just show everything cut in half and juxtaposed [did I spell that right?]
Bill

---

### Post by gerbman on 2006-08-17
> **Ragzouken said:**
> What I mean is, in Xinerama, it's always using the left screen to put the Taskbar/Workspace bar, and the Applications/Places/System/Time-Date on, I can seem to get them on the right screen whatever I do.Ahhhh, I understand. Well my xorg.conf file doesn't use Xinerama. The result of my xorg.conf is a dual-head setup where each monitor has its own applications menu, taskbar, etc. I'm not familiar with Xinerama. I generated my xorg.conf file with the aticonfig program included with the driver:```
sudo aticonfig --initial=dual-head --screen-layout=right
```Type 'aticonfig' to get a complete list of options.

---

### Post by Ragzouken on 2006-08-17
Switching cables is not an option, as I have them set up like they are now so that windows will do it right, surely there is some way to pretend I have switched the cables with some option in the file?

Also, I've switched to non-xinerama now (non-xine or xine is not the problem  I think) and something has gone terribly wrong. The only sound I can get is Squealing, and the taskbar etc is taking an age to load, with terminal also taking ages to be ready for use after I've opened it.

---

### Post by gerbman on 2006-08-17
> **Ragzouken said:**
> Switching cables is not an option, as I have them set up like they are now so that windows will do it right, surely there is some way to pretend I have switched the cables with some option in the file?

Also, I've switched to non-xinerama now (non-xine or xine is not the problem  I think) and something has gone terribly wrong. The only sound I can get is Squealing, and the taskbar etc is taking an age to load, with terminal also taking ages to be ready for use after I've opened it.You can create the default xorg.conf with:```
aticonfig --force --initial -o ~/xorg.conf
```it will create the file in your home directory.

---

### Post by Ragzouken on 2006-08-18
Well my sound problems etc have seemed to fix overnight, but, for some reason, the cursor won't change on the right screen, no I for text, and hand cursor for links.

---

### Post by gerbman on 2006-08-18
> **Ragzouken said:**
> Well my sound problems etc have seemed to fix overnight, but, for some reason, the cursor won't change on the right screen, no I for text, and hand cursor for links.Strange...I've no clue...

---

