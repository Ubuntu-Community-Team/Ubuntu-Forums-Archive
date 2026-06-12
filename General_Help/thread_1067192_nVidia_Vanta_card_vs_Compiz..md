---
title: "nVidia Vanta card vs Compiz."
date: 2009-02-11
forum: General Help
---

### Post by rick71 on 2009-02-11
Can someone help me get Compiz running?

I have an nVidia NV6 [Vanta/Vanta LT] card. The nvidia-glx-legacy is installed. Compiz is installed. I have a fresh install of Ubuntu 8.04 with all updates. It seems Compiz will not start. When I try to start compiz in a terminal I get the following:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:002c (rev 15) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

MY xorg.conf has the following:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		"UseEdidFreqs"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

Does anyone have any suggestions for getting Compiz to work? Any and all help appreciated.

---

### Post by rick71 on 2009-02-11
I just saw the post witch check-compiz. I have installed it and got the following:

```

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...
ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required
       version is 1.11.

./compiz-check: line 741: [: : integer expression expected
           [ OK ]


```

I hope this helps.

---

