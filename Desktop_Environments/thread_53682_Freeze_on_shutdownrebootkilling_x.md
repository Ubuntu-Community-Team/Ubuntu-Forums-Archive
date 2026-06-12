---
title: "Freeze on shutdown/reboot/killing x"
date: 2005-08-01
forum: Desktop Environments
---

### Post by BobLot on 2005-08-01
When I try to shutdown/reboot/kill x everything freezes. Only way to fix is a hard reboot (reset button on the case). This happens every time I try to shutdown ubuntu.

I think it may have something to do with Twinview.
Anyway, here's my xorg.conf 
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
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
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
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
	Option "TwinView" "true"
	Option "TwinViewOrientation" "Clone"
	Option "TVOutFormat" "COMPOSITE"
	Option "TVStandard" "PAL-G"
	Option "SecondMonitorHorizSync" "30-50"
	Option "SecondMonitorVertRefresh" "60"
	Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;  512x384,512x384"
EndSection

Section "Monitor"
	Identifier	"Philips 107B"
	VendorName	"Philips"
	ModelName	"107B(17inch/CM6800)"	
	Option		"DPMS"
	HorizSync	30-69
	VertRefresh	50-139
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Monitor		"Philips 107B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
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

Also, does anybody have suggestions on how to get 100hz refresh rate @ 1024x786?

thanks in advance for any answers.

---

### Post by BobLot on 2005-08-02
anybody?

---

### Post by InvIsiBlekID on 2005-09-14
im having the same problem, any help would be appreciated!!

---

### Post by Widdershins on 2005-09-17
I have this problem as well.  

Xorg.conf:
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
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
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
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	Option		"IgnoreDisplayDevices"	"TV"	
	Option		"UseInternalAGPGART"	"no"
	Option		"MonitorLayout"		"LCD, LCD"
EndSection

Section "Monitor"
	Identifier	"DELL E171FPb"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"DELL E171FPb"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
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


Any help would be much appreciated!

---

### Post by raoul110 on 2005-10-08
i have the same problem since the update of nvidia glx anything 6xxx to 7xxx and the kernel 2.8 to kernel 2.12.
i have no twinview, only the default xorg.conf.
i have probed everything, deinstalled the nvidiapackage and installed the latest version direct from the nvidia package, every newest kernel-image with the newest nvidia-package, no success still the freeze at shutdown.

i have kubuntu breezy installed, daily dist-upgrade, with amd xp+2000 and a nvidia fx5700ultra.

thanks for any hints,

markus

---

### Post by raoul110 on 2005-10-08
i had forgotten an important hint:

the freeze is only with the nvidia-driver,
with the nv driver there is no problem, everything normal and no freeze.

so i think there is a problem between the kernel and the nvidia-driver.
more kernel than nvidia, but i don´t known...

and there is no log record in any log-file

thanks,

markus

---

### Post by kohai on 2005-12-01
UP ! 

Hi everyone, I just installed Breezy, and i have the exect same problem !!

Freeze on Reboot/Logout, which forces me to make a 'hard reset' :(

Using the NVidia drivers, and the K7-kernel ( though it's the same with the 386 kernel, already tested )

Any ideas / thoughts / help is appreciated ! :)

---

### Post by kohai on 2005-12-03
Oh, and i forgot to say that i have a fx5700 Ultra also ! :)

---

