---
title: "ATI fglrx 8.18.8, Big desktop resolution/hz problem"
date: 2005-11-07
forum: Desktop Environments
---

### Post by Morrigu on 2005-11-07
Hi , and sorry for troubling you all with these silly ATI problems :)

I spent LOTS of time to get my dual screen working properly, finally with 8.18.8 fglrx drivers inbuilt xinerama (big desktop, horizontal) I was able to get almost what I wanted.

[http://ameba.lpt.fi/~lindmmik/linux/Screenshot.jpg]("http://ameba.lpt.fi/~lindmmik/linux/Screenshot.jpg")

Though that may look nice as a screenshot, my eyes are pretty much bleeding because the monitor on the right is running 1280 x 1024 @ 60Hz :( It's an old monitor and can't do any better. What I'm looking is either running both displays at 1024 x 768, or running them both at different resolutions.

Inbuilt xinerama in fglrx shows that my current resolution is 2560 x 1024. This is somehow automatically detected, this resolution isn't in my xorg.conf. How can I change this resolution?

My current xorg.conf :
```

Section "Device"
	Identifier	"ATI"
	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	Option		"UseInternalAGPGART"	"no"
	Option		"no_accel" 		"no"
	Option		"no_dri"		"no"
	Option		"mtrr"			"off"
    	Option 		"DesktopSetup"          "Horizontal"
	Option		"MonitorLayout"		"AUTO, AUTO"
	Option		"MetaModes"		"1280x1024-1024x768"
	Option		"IgnoreEDID"		"off"
	Option		"NoTV"			"no"
	BusID		"PCI:3:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI2"
	Driver		"fglrx"
	BusID		"PCI:3:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"SAMTRON"
	HorizSync    	30-96
	VertRefresh  	50-85
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"COMPAQ"
	HorizSync    	30-96
	VertRefresh  	50-75
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI"
	Monitor		"SAMTRON"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Option		"Clone"		"off"
	Screen		0 "Default Screen" 0 0 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

ATI really keeps changing the way xorg.conf works in every version of their drivers, makes googling for help very difficult :( Thanks for any help you can give me!

---

### Post by Inspector Hector on 2005-11-07
Did you tried it with a second "screen", where you could put some different modes?

Something like

```

[...]

Section "Screen"
   Identifier"Default Screen"
   Device"ATI"
   Monitor"SAMTRON"
   DefaultDepth24
   SubSection "Display"
      Depth24
      Modes"1280x1024" "1024x768" "800x600"
   EndSubSection
EndSection

Section "Screen"
   Identifier"Another Screen"
   Device"ATI"
   Monitor"COMPAQ"
   DefaultDepth24
   SubSection "Display"
      Depth24
      Modes"1280x1024" "<Something different here>" "800x600"
   EndSubSection
EndSection

[...]

```

Oh, and just to mentioned it, it didn't worked for me very well :-)
But i have a very specific case, so give it a try (if you did not already)

---

