---
title: "Lock"
date: 2006-05-26
forum: Desktop Environments
---

### Post by Blairboy on 2006-05-26
Ok, I followed the xglati wiki and I can't fix the locking problem.  I have an ati x1600xt.  Please tell me what I need to change to fix this crapola.  I really wanna try out compiz.

Here's part of my xorg.conf:

Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fglrx"
	BusID		"PCI:5:0:0"
	Option		"UseFBDev"		"true"
   	Option       	"no_accel" "no"
	Option       	"no_dri" "no"
	Option       	"DynamicClocks" "on"
	Option       	"mtrr" "on"
	Option       	"DesktopSetup" "Single"
	Option       	"ScreenOverlap" "0"
	Option       "Capabilities" "0x00000000"
	Option       "CapabilitiesEx" "0x00000000"
	Option       "VideoOverlay" "on"
	Option       "OpenGLOverlay" "off"
	Option       "CenterMode" "off"
	Option       "PseudoColorVisuals" "off"
	Option       "Stereo" "off"
	Option       "StereoSyncEnable" "1"
	Option       "FSAAEnable" "no"
	Option       "FSAAScale" "1"
	Option       "FSAADisableGamma" "no"
	Option       "FSAACustomizeMSPos" "no"
	Option       "FSAAMSPosX0" "0.000000"
	Option       "FSAAMSPosY0" "0.000000"
	Option       "FSAAMSPosX1" "0.000000"
	Option       "FSAAMSPosY1" "0.000000"
	Option       "FSAAMSPosX2" "0.000000"
	Option       "FSAAMSPosY2" "0.000000"
	Option       "FSAAMSPosX3" "0.000000"
	Option       "FSAAMSPosY3" "0.000000"
	Option       "FSAAMSPosX4" "0.000000"
	Option       "FSAAMSPosY4" "0.000000"
	Option       "FSAAMSPosX5" "0.000000"
	Option       "FSAAMSPosY5" "0.000000"
	Option       "UseFastTLS" "0"
	Option       "BlockSignalsOnLock" "on"
	Option       "UseInternalAGPGART" "no"
	Option       "ForceGenericCPU" "no"
	Option       "KernelModuleParm" "agplock=0"
	Option       "PowerState" "1"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

---

### Post by Blairboy on 2006-05-26
Everybody stumped?

---

### Post by Blairboy on 2006-05-26
20 views and everyone's stumped?

---

