---
title: "help with dual monitor... it is sort of working..."
date: 2006-09-30
forum: Desktop Environments
---

### Post by kpm on 2006-09-30
after editing my xorg.conf file, I was finally able to restart Xorg without any errors.  However, I am getting strange behaviour... I have an old 19inch crt KDS VisualSensations 190i that I plugged into my old IBM Thinkpad A22m laptop.  On both screens, I have some horizontal lines moving up the screen (much worse on the laptop - as well the laptop has a great deal of them much closer together and moving rapidly up the screen).  The laptop screen is also split about one quarter of the way from the right and mirroring about a one inch section of the far left of the laptop screen, then blank.  Then there is a noisy area (the many horizontal lines running up the screen) then the rest of the laptop screen seems fine.  Hard to describe... I tried to take a screen shot but I only get the 19inch crt in the result with a blank space beside it...  Anyway, the following is my edited section to the xorg.conf file, if anyone could help you will save my eyes a great deal of strain!!
Thanks
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
	Monitor		"Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
	Monitor		"Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"Twin HEad"
	Screen		"Main Screen"
	Screen		"Second Screen" LeftOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Ziox on 2006-09-30
> **kpm said:**
> after editing my xorg.conf file, I was finally able to restart Xorg without any errors.  However, I am getting strange behaviour... I have an old 19inch crt KDS VisualSensations 190i that I plugged into my old IBM Thinkpad A22m laptop.  On both screens, I have some horizontal lines moving up the screen (much worse on the laptop - as well the laptop has a great deal of them much closer together and moving rapidly up the screen).  The laptop screen is also split about one quarter of the way from the right and mirroring about a one inch section of the far left of the laptop screen, then blank.  Then there is a noisy area (the many horizontal lines running up the screen) then the rest of the laptop screen seems fine.  Hard to describe... I tried to take a screen shot but I only get the 19inch crt in the result with a blank space beside it...  Anyway, the following is my edited section to the xorg.conf file, if anyone could help you will save my eyes a great deal of strain!!
Thanks
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
	Monitor		"Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
	Monitor		"Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"Twin HEad"
	Screen		"Main Screen"
	Screen		"Second Screen" LeftOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

try switching the sets of HorizSync and VertRefresh...

---

### Post by wieman01 on 2006-09-30
I had the same problem. You'll have to do this:

1. Change "Device" settings:
> Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	[COLOR="Red"]Option		"MonitorLayout"	"CRT,LFP"[/COLOR]
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	[COLOR="Red"]Option		"MonitorLayout" "CRT,LFP"
	Option		"TVOutFormat" "Composite"[/COLOR]
	Screen		1
EndSection
2. Add another line here:
> Section "ServerLayout"
	Identifier	"Twin HEad"
	Screen		"Main Screen"
	Screen		"Second Screen" LeftOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	[COLOR="Red"]Option		"Xinerama" "true"
[/COLOR]EndSection
There is more stuff here: [http://www.ubuntuforums.org/showthread.php?t=221908&highlight=sony+vaio+xinerama]("http://www.ubuntuforums.org/showthread.php?t=221908&highlight=sony+vaio+xinerama")

Let us know how it goes.

---

### Post by wieman01 on 2006-09-30
Wait a second! Made a mistake!

**_EDIT:_**
Ok, done. Sorry... It's ok now.

---

### Post by kpm on 2006-10-01
> **Ziox said:**
> try switching the sets of HorizSync and VertRefresh...
Thanks for the input!  A fruther question though... When you say 'switching the sets...' do you mean applying those from the laptop to the crt?? Or do you mean just to try different values for these?

---

### Post by kpm on 2006-10-01
> **wieman01 said:**
> Let us know how it goes.

I added those values, restarted, still same problems though...
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"MonitorLayout" "CRT,LFP"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MonitorLayout" "CRT,LFP"
	Option "TVOutFormat" "Composite"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
	Monitor		"Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
	Monitor		"Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"Twin Head"
	Screen		0 "Main Screen"
	Screen		1 "Second Screen" LeftOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Ziox on 2006-10-01
> **kpm said:**
> I added those values, restarted, still same problems though...
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"MonitorLayout" "CRT,LFP"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MonitorLayout" "CRT,LFP"
	Option "TVOutFormat" "Composite"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
	Monitor		"Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
	Monitor		"Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"Twin Head"
	Screen		0 "Main Screen"
	Screen		1 "Second Screen" LeftOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

What I meant is this. Switch this set of numbers:
[PHP]HorizSync       30-65
VertRefresh     50-75[/PHP]

with these numbers:
	[PHP]HorizSync	30-95
	VertRefresh	50-120[/PHP]
and
	[PHP]HorizSync	28-70
	VertRefresh	43-60[/PHP]

---

### Post by kpm on 2006-10-01
gave it a go, but still no improvement...

---

### Post by wieman01 on 2006-10-01
> **kpm said:**
> gave it a go, but still no improvement...
Try the solution I have suggested. Apparently there is something wrong with your Xinerama setup in xorg.conf. That's all I can say.

---

