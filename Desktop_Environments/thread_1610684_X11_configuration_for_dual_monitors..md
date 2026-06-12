---
title: "X11 configuration for dual monitors."
date: 2010-11-01
forum: Desktop Environments
---

### Post by enochthered on 2010-11-01
Hi everyone,

I have a brand new installation of Ubuntu 10.10. I'm using a GeForce 8600GT graphics chipset.

I have two monitors, and my goal here is to have them both working under Ubuntu in their full resolutions, and I've not had any luck with this yet. I've got a Viewsonic VE155s with a native resolution of 1024x768, and a Chimei CMV 221D with a native resolution of 1680x1050. 

When I first installed Ubuntu, both monitors were working, and the VE155s was working in its native resolution of 1024x768, but the CMV221D was stuck in 640x480. 

The Nvidia video configuration utility was not identifying the latter monitor - it only reported it as DFP-0, and doesn't allow any resolution above 640x480 to be set. The mechanism (which has a name which I don't recall) which allows the OS to interrogate the monitor's firmware to find out the monitor manufacturer, model and accepted resolutions and frequencies to use does not seem to have worked.

(I previously had the Nvidia driver installed, but I've since switched back to the default open source vesa driver. I won't use the closed Nvidia driver if I don't need to, but if I need to use it to get acceptable performance from this hardware than I will.)

So I did a little bit of reading and I did some hacking of xorg.conf.

Previously I had the 15" monitor working in 1024x768 and the 22" 
monitor working in 640x480.

Now I've got the 22" monitor working in 1680x1050 as desired, and the 15" monitor not working at all.

Here's a copy of my xorg.conf. For the sake of brevity I have not included the unnecessary bits such as input devices.

Can somebody help point out what I've overlooked, so I can get both monitors working?

Cheers :)

```

Section "Device"
	Identifier "NVidia"
#	Driver "nvidia"
	Driver "vesa"
	VendorName "NVIDIA Corporation"
	BoardName "GeForce 8600GT"
	
	Option "CursorShadow" "1"
	Option "CursorShadowAlpha" "63"
	Option "CursorShadowYOffset" "2"
	Option "CursorShadowXOffset" "4"
	Option "FlatPanelProperties" "Scaling = native"
	Option "NoLogo" "true"
	Option "IgnoreEdid" "true" # needs to be true for some nvidia cards
EndSection

Section "Monitor"
        Identifier	"VE155s"
        VendorName	"Viewsonic"
        ModelName	"ViewSonic VE155s"
        HorizSync	30.0 - 62.0
        VertRefresh	50.0 - 75.0
        Option	"DPMS"

	Modeline "1024x768" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
#	Modeline "1024x768" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
#	Modeline "1024x768" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
EndSection

Section "Monitor"
        Identifier "CMV221D"
        VendorName "Chimei"
        ModelName "CMV221D"
        HorizSync 30.0 - 82.0
        VertRefresh 56.0 - 76.0
	Option	"DPMS"	
	
	Mode "1680x1050"
                DotClock 149.00	 
                HTimings 1680 1760 1944 2280 
                VTimings 1050 1050 1052 1089 
                Flags "+HSync" "+VSync"
        EndMode
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"NVidia"
        Monitor		"VE155s"
	DefaultDepth 24
	
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
	
	Option "TwinView" "1"
#	Option "MetaModes" "VE155s: 1024x768 +0+0, CMV221D: 1680x1050 +1024+0"
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"NVidia"
        Monitor		"CMV221D"
	DefaultColorDepth 24
	
	SubSection "Display"
		Depth 24
#		Modes "1680x1050"
	EndSubSection
	
	Option "TwinView" "1"
#	Option "MetaModes" "VE155s: 1024x768 +0+0, CMV221D: 1680x1050 +1024+0"
EndSection

Section "ServerLayout"
	Identifier	"DefaultLayout"
	Screen		"Screen1"
	Screen		"Screen0" LeftOf "Screen1"

    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection


```

---

### Post by enochthered on 2010-11-02
Nobody? I would really appreciate some help with this.

---

