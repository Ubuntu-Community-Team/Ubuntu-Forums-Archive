---
title: "dualhead with openbox - can't get menus on second screen"
date: 2006-03-05
forum: Desktop Environments
---

### Post by guano on 2006-03-05
So, I've been using OpenBox for the last two or three weeks now. It's really lightweight and fast. I am with a very minimalist desktop now (just a wallpaper and conky), I edited the menus and make a second menu called "Toolbar" where I put my most used apps.

The problem is abou dualhead configuration. I already managed to get it working, but when I am using the TV as a second monitor (S-VIDEO output), in openbox, I don't get the wallpaper on the TV. worse than that, I don't have the menu! no matter what button I click, there's no menu... :( 

I guess it is something about OB, since I can log into GNOME, and get everything, wallpaper, menus, all!

Can anyone with larger experience in OpenBox (or BlackBox, FluxBox, AnyBox..) help me on this? I don't want to need to log into gnome just to watch dvd on tv.


my xorg.conf:

```

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout" "CRT,LFP"
	Screen 1
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD_TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Screen 0
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Option "TVStandard" "PAL-M"
	Option "TVOutFormat" "SVIDEO" # "Composite" or "SVIDEO" or "RBG"
	Option "ConnectedMonitor" "TV" 
	Screen 1
	BusId "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
EndSection


Section "Monitor"
	Identifier "TV"
	HorizSync	30-50
	VertRefresh 60
EndSection

Section "Screen"
	Identifier	"LCD_CRT"
	Device		"LCD_CRT"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"LCD_TV"
	Device		"LCD_TV"
	Monitor		"LCD"
	DefaultDepth	24
	Subsection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "CRT"
	Device "CRT"
	Monitor "CRT"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1024x768"
	EndSubsection
EndSection

Section "Screen"
	Identifier "TV"
	Device "TV"
	Monitor "TV"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1024x768" "800x600"
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier "LCDandTV"
	Screen 0 "LCD_TV"
	Screen 1 "TV" RightOf "LCD_TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier "LCDandCRT"
	Screen 0 "LCD_CRT"
	Screen 1 "CRT" RightOf "LCD_CRT"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	Option "DefaultServerLayout" "LCDandTV"
#	Option "DefaultServerLayout" "LCDandCRT"
EndSection


Section "DRI"
	Mode	0666
EndSection

```

---

