---
title: "TV-out configuration"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Xailia on 2006-09-19
I am running Ubuntu 6.06 for the purpose of a mythtv box.  The system specifications are:
PIII 1 gig
512 MB SDRAM
Geforce4 4400 (With svideo, coax, and component outs)

Here is the display portion of my Xconfig file:
```
Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4400]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I have searched and was unable to find a guide for how to properly configure a normal television within ubuntu.  I currently have the card outputing the signal over the svideo out and it does display on the screen.  The problem is that the display is not calibrated correctly so portions of the windows run off the screen.  Because of this I can't access some of the buttons on the UIs and hence am unable to use the programs.

I realise this description is fairly vague; if there is any information that would be helpful let me know...any help would be appreciated.

---

### Post by whitewizardcoder on 2006-09-19
Hope this helps...

[https://help.ubuntu.com/community/NvidiaTVOut]("https://help.ubuntu.com/community/NvidiaTVOut")

-WhiteWizardCoder

---

