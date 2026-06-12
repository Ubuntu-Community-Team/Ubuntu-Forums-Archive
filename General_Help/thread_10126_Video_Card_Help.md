---
title: "Video Card Help"
date: 2005-01-05
forum: General Help
---

### Post by MaTZ! on 2005-01-05
I have a nvidia fx 5700. [-X 
I have installed all the drivers correctly!

I have installed two different Monitors:  a LCD (sony) and a CRT(philips).

Because i like the dual heads option i have modified the XFRE.... config and i have enabled the "TwinView" option.

Now all works !!!

This is the CFG:
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
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
	Identifier	"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "RenderAccel"           "true"
        Option          "NvAGP"                 "1"
	Option 		"TwinView"		"true"
	Option		"MetaModes" 		"1280x1024,1280x1024; 1024x768,1024x768"
	Option 		"HorizSync"  "CRT-0: 50-110;  DFP-0: 40-70"
	Option 		"VertRefresh"  "CRT-0: 60-120;  DFP-0: 60"
	Option 		"ConnectedMonitor"	"DFP-0,CRT-0"
	Option 		"TwinViewOrientation"	"CRT-0 RightOf DFP-0"

EndSection

Section "Monitor"
	Identifier	"Philips 107P"
	HorizSync	30-96
	VertRefresh	50-160
	Option		"DPMS"

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
	Monitor		"Philips 107P"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
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


Then i tried to add the TV (tvout). First I tried adding :

```

        Option 		"HorizSync"  "CRT-0: 50-110;  DFP-0: 40-70;TV: 30-80"
	Option 		"VertRefresh"  "CRT-0: 60-120;  DFP-0: 60;TV: 50-60"
	Option 		"ConnectedMonitor"	"DFP-0,CRT-0,TV"
	Option 		"TwinViewOrientation"	"CRT-0 RightOf DFP-0"
``` 

and the mode Pal-B (for italian Format).

I tryed this configuration and it doesn't work. X11 doesn't Start.

So i thought that is a problem with the 3 monitor connected (lcd + crt + TV).

So i made a new account (with Fluxbox interface ONLY TO SEE DVD on MY TV)
and i made a new Config (TV + CRT [clone mode]).

This is the new Config:
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
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
	Identifier	"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "RenderAccel"           "true"
        Option          "NvAGP"                 "1"
	Option 		"TwinView"		"true"
	Option		"MetaModes" 		"1280x1024,1280x1024; 1024x768,1024x768"
	Option 		"HorizSync"  "CRT-0: 50-110;  TV: 30-50"
	Option 		"VertRefresh"  "CRT-0: 60-120;  TV: 50-60"
	Option 		"ConnectedMonitor"	"CRT-0,TV"
	Option 		"TwinViewOrientation"	"CRT-0 clone TV"
	Option 		"TVStandard"		"PAL-G"	
EndSection

Section "Monitor"
	Identifier	"Philips 107P"
	HorizSync	30-96
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
	Monitor		"Philips 107P"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
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

Now the TVOUT Works But there is a problem. The TV doesn't Display Colours (it's only BLACK & WHITE ).


Can You HELP me plz?  O:) 

thanks
(sorry for my english  :-# ).

---

### Post by MaTZ! on 2005-01-06
up!

 ](*,)

---

### Post by daniels on 2005-01-09
I guess the problem might be that you've only attached S-Video when you need to attach both S-Video and RCA to the TV -- this will happen with VCRs and stuff as well.  Beyond that, I don't know; I don't own an nVidia card with TV out on it.

---

### Post by aranbanjo on 2005-01-14
Yes,
you need a little cable to convert S-Video to RCA.

---

