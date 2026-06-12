---
title: "Monitor and Nvidia"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Das Oracle on 2006-07-19
I've been having issues with my monitor and I've narrowed down the problem a bit for you all. here we go: My monitor will not stop flickering and the problem is caused by my refresh rate being to high for my given resolution. here are some specs:


card:            nvidia geforce fx 5200 w/ 256MB
monitor:         samsung syncmaster 730B
drivers:         nvidia-glx from the repositories
screen settings: 1280x1024@75


the manual for my monitor says that at 1280x1024 my refresh rate should be 60Khz. When I use the nv drivers for xorg I can change the refresh rate of the monitor down from 75 to 60, but the problem is when I use the nvidia driver in xorg.conf I am not given the 60hz option and am stuck with the 75Khz option. This is where I'm stuck and I'll leave with this snippet from xorg.conf.

```

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"SyncMaster"
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
```


Thanks in advance

---

### Post by orb9220 on 2006-07-19
your line VertRefresh	50-75
change to 60 no range That is mine using an fx5200 card and older monitor

---

### Post by orb9220 on 2006-07-19
hope I worded right change the 50-75 value to just 60

---

### Post by mlind on 2006-07-19
For my Samsung flat panel and newest nvidia drivers, I need to request custom modeline for 60Hz to work.

```

 SubSection "Display"
                Depth           24
                Modes           **"1280x1024_60"** "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection

```

---

### Post by Das Oracle on 2006-07-20
I tried both suggested ideas neither setting refresh to just 60 or setting my own custom modeline worked

---

### Post by Das Oracle on 2006-07-20
Here is something very interesting I found out....my monitor is a flatpanel but when I run 'sudo xresprobe nvidia' it tells me this:

```
id: SyncMaster
res: 1280x1024 1152x864 1024x768 832x624 800x600 720x400 640x480
freq: 30-81 56-75
disptype: crt

```

could the fact that its picking up as a crt make a difference?

---

### Post by mlind on 2006-07-20
> **Das Oracle said:**
> Here is something very interesting I found out....my monitor is a flatpanel but when I run 'sudo xresprobe nvidia' it tells me this:

```
id: SyncMaster
res: 1280x1024 1152x864 1024x768 832x624 800x600 720x400 640x480
freq: 30-81 56-75
disptype: crt

```

could the fact that its picking up as a crt make a difference?

No, I recall it does that if your panel is not connected using the DVI input.
Using that custom modeline should really work. Here's part of my /etc/xorg.conf

```

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"TVOut"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"TVOutFormat"		"COMPOSITE"
	Option		"TVStandard"		"PAL-B"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

Section "Monitor"
	Identifier	"Television"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		8
		Modes		**"1280x1024_60"** "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		**"1280x1024_60"** "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		**"1280x1024_60"** "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TVScreen"
	Device		"TVOut"
	Monitor		"Television"
	SubSection "Display"
		Depth		24
		Modes		"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Default Screen"
	Screen 1	"TVScreen" LeftOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

---

