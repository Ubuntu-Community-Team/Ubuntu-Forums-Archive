---
title: "refresh rate low! monitor screen flashing hurts eyes"
date: 2009-01-28
forum: General Help
---

### Post by sdowney717 on 2009-01-28
making any changes to the refresh rate has no effect

Running an ati x1300

Otherwise, it is working as it should be. I want a refresh of 85 and it feels like it is 60 hz.

anything in here a problem?

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	Option	    "AIGLX" "true"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "IgnoreABI" "True"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "AccelMethod" "EXA"
	Option	    "AccelDFS" "off"
	Option	    "AGPMode" "4"
	Option	    "AGPFastWrite" "1"
	Option	    "EnablePageFlip"
	Option	    "ColorTiling"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

---

### Post by sdowney717 on 2009-01-28
I just solved it by taking out that junk from xorg.cong

	Option	    "AccelMethod" "EXA"
	Option	    "AccelDFS" "off"
	Option	    "AGPMode" "4"
	Option	    "AGPFastWrite" "1"
	Option	    "EnablePageFlip"
	Option	    "ColorTiling"
	BusID       "PCI:1:0:0"

---

