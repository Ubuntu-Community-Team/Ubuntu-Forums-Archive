---
title: "External monitor not working - D620, Nvidia, Dport Replicator, Monitor"
date: 2008-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jamesjwilsonsr on 2008-06-30
First, I am a total newb, so bear with me   :D  
Let me tell you my goal, and maybe my details are irrelevant if you just know what I want to do.

I am docking and undocking about thrice a day.  I need to be able to dock, close my laptop, and see my screen on my external monitor.  Then, undock, and see my screen on my laptop display.  With that said, here are some details:

I am running Hardy 8.04 x64.

I have the following hardware:
Dell D620
Nvidia video
D Port replicator
external Dell Monitor (2007wfpb)

When I power on the laptop (docked) I see on the external monitor the grub loader then the Ubuntu logo with the progress bar.  After that, the monitor flashes and I assume XWindows starts and it doesn't quite know what to do.  It goes to power saving mode and the laptop's display becomes the active monitor.  Hitting ctrl + alt + f1-f6 gives me the login prompt on the external monitor, f7 sends me back to the laptop's display.


I did some searching and found [this]("http://ubuntuforums.org/showthread.php?t=763883") thread which seems close to my scenario, but I am just not sure what to do.  Honestly, I need a bit of hand holding on this one.

Here is my Xorg.conf file:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 110M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewOrientation" "rightof"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Thanks for any help in advance.

---

### Post by jamesjwilsonsr on 2008-07-01
I ran the EnvyNG utility by Tseliot (linked to [here]("http://ubuntuforums.org/showthread.php?t=301499")).

As a result, my xorg.conf file is modified from my first post:

```

Section "Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
	Option		"TwinViewOrientation"	"rightof"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Device0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"Quadro NVS 110M"
EndSection

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
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Screen0" 0 0
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
	Inputdevice	"Configured Mouse"	"CorePointer"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"Unknown"
	Horizsync	30.0	-	110.0
	Vertrefresh	50.0	-	150.0
	Option		"DPMS"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

Now the external monitor says "No VGA cable" and even while booting into Ubuntu, or if I hit Ctrl + Alt + F1-F6...it is only on the laptop display.

Thanks again for any help.

---

### Post by jamesjwilsonsr on 2008-07-01
> **jamesjwilsonsr said:**
> I did some searching and found [this]("http://ubuntuforums.org/showthread.php?t=763883") thread which seems close to my scenario, but I am just not sure what to do.  

Ok, I fixed it.

My problem was that the link above (which I followed the directions of) was for the DVI, not VGA connection to the replicator.  Once I switched out the cables, it worked! ](*,)

Here is what I added to my xorg.conf file under the **Section "Screen"** section:

```

Section "Screen"
[B]	#Option		"ConnectedMonitor" "DFP-1, DFP-0"
	Option		"UseDisplayDevice" "DFP-1, CRT"
	Option		"MetaModes" "nvidia-auto-select"
	Option		"AllowGLXWithComposite" "True"
	Option		"RenderAccel" "True"
	Option		"AddARGBGLXVisuals" "True"
	DefaultDepth	24
	SubSection     "Display"
		Depth       24[/B]
	EndSubSection

```

---

### Post by Wolfhere on 2008-11-14
Dude, you are awesome. I have been leaving my laptop open in the dock and doing the Fn-F8 thing for months. This worked for me. I have edited the xorg.conf several times without resolution. this worked for me.

Thank you:guitar:

---

