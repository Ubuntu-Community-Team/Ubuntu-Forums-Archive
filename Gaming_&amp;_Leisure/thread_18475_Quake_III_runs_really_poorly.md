---
title: "Quake III runs really poorly"
date: 2005-03-07
forum: Gaming &amp; Leisure
---

### Post by nashife on 2005-03-07
I just installed quake III, but for some reason it runs extremely poorly.  sound and video are both very glitchy.  

as far as I know, I've got nvidia drivers installed correctly though.  Enemy Territory works fine and runs smoothly.

I've tried searching the forums and google for others who have the same problem, but I'm not finding anything... 

How can I diagnose the problem?  I'm still learning ubuntu and linux in general.

---

### Post by jdodson on 2005-03-07
[QUOTE=nashife]I just installed quake III, but for some reason it runs extremely poorly.  sound and video are both very glitchy.  

as far as I know, I've got nvidia drivers installed correctly though.  Enemy Territory works fine and runs smoothly.

I've tried searching the forums and google for others who have the same problem, but I'm not finding anything... 

How can I diagnose the problem?  I'm still learning ubuntu and linux in general.[/QUOTE]


sorry to hear that.  post your X11 conf file.  run glxgears, what are kind of FPS are you getting?  what kind of nvidia card is it?

---

### Post by nashife on 2005-03-07
[QUOTE=jdodson]sorry to hear that.  post your X11 conf file.  run glxgears, what are kind of FPS are you getting?  what kind of nvidia card is it?[/QUOTE]

I'm still learning ubuntu.  Where would my X11 config file be? what would it be called?

I'll run glxgears as soon as I get home...

and it's a gforce 4 card.

---

### Post by Dylanby on 2005-03-08
Your config would be in /etc/X11 named XF86Config-4

Try starting the game from a terminal & note any errors.

---

### Post by nashife on 2005-03-10
It's the week before finals, so I got pretty busy the last few days and wasn't able to follow your advice until now. Sorry sorry! I really appreciate people responding!

I ran glxgears, and I'm getting between 7.000 and 12.000 fps!!  (wtf?! I was getting much better fps before I installed the nvidia drivers!)  

I'm figuring that this is a sign that opengl is very unhappy... I thought Enemy Territory also used OpenGL... why would it work if OpenGL isn't working?

I ran quake3 from the terminal, and there were no errors printed when I quit.

at the end of this post is my XF86Config-4 file (the parts after the commented out section).

Thanks for responding and offering help. again, sorry I didn't follow up until now. 

Emily
```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
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
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	HorizSync	30-61
	VertRefresh	56-75
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
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
```

---

### Post by nashife on 2005-03-10
some bad bad things....  

I've just discovered that Enemy Territory now no longer works... it worked before I installed quake, and now it doesn't.

This makes more sense...  seems openGL is broken completely...


**Edit:**  I can't explain this... maybe someone else can give me insight... but the problem fixed itself.  I rebooted a second or third time and now I'm getting around 1000.00 fps, and both quake and ET work fine now.

perhaps today is just not my day. :)

Thanks guys...

---

### Post by Slapdash on 2005-03-11
Yep, I rekon the old PC spirits are sometimes full of mischief ;)

Glad to see you got it working in the end

---

### Post by dermotti on 2005-03-11
Comment out the two lines glcore and dri


Section "Module"
#     Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#     Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"

---

