---
title: "KDE - Starts in Low Resolution"
date: 2006-01-05
forum: Desktop Environments
---

### Post by mpa on 2006-01-05
I am using Kubuntu Breezy with KDM as login manager, with auto-login option turned on. Every now and then ; actually about half of the time ; when starting X and KDE, instead of the usual resolution 1024 x 768,  it uses a v```

```ery low resolution instead, everything is so big and block so that I usually just had to restart X. When restarted it always reset the resolution back to 1024 x 768. But, can anyone help me identify the problem, it is rather annoying having to restart X repeatedly. ;)

My configuration is :
Kubuntu 5.10
Kernel : Linux 2.6.12-10-k7 
Athlon 64 3000+ / 768MB RAM
MSI Nvidia 6600GT 128MB
KDE 3.5 (upgraded using packaged in kubuntu repository)


```

xorg.conf :

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
	Option		"XkbLayout"	"ch"
	Option		"XkbVariant"	"de"
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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"SAMTRON"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"SAMTRON"
	DefaultDepth	24
	Option		"NoLogo" "True"
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

---

### Post by mo_x on 2006-01-05
For the nvidia driver the following 2 lines should be removed.
Load	"GLcore"
Load	"dri"
I don't know about the resolution problem but you can change the resolution by pressing Ctrl+Alt+"+" or Ctrl+Alt+"-".

---

