---
title: "Weird mouse pointer problem"
date: 2008-02-01
forum: Desktop Environments
---

### Post by djgenesis on 2008-02-01
Ok, this is totally crazy. 

I have dual head setup on my Kubuntu 7.10 Xinerama enabled on my ATi Radeon 9500. 
I am using FGLRX drivers and I have a very weird mouse problem. 

Whenever I am moving a window around by clicking the left mouse button, the pointer, from arrow, turns into a hand. When I release the button, the pointer turns back into arrow.

But when I am moving a window from the main monitor to the secondary, the pointer turns into a "hand" while moving the window to the other screen, but doesn't change back! 
Even if I select some text, the pointer does not turn into a | symbol. 

It only reverts to normal, if I release the window I was moving on the secondary screen, move the mouse to my primary screen and bring it back to the secondary. 

I hope this makes sense. 

Has anyone seen this before? 

xorg.conf
```



Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
#	Option	    "Device" "/dev/input/mice"
#	#Option	    "Protocol" "ImPS/2"
#	#Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection


Section "Monitor"
        Identifier "Sony_Left"
        Option  "DPMS"
EndSection

Section "Monitor"
        Identifier "Sony_Right"
        Option  "DPMS"
EndSection

Section "Device"
        Identifier      "ati0"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Screen         0 
EndSection

Section "Device"
        Identifier      "ati1"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection

Section "Screen"
	Identifier "screen0"
        Device          "ati0"
        Monitor         "Sony_Left"
        DefaultDepth    24
	SubSection "Display"
		Modes    "1280x1024" "1280x960" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "screen1"
	Device     "ati1"
	Monitor    "Sony_Right"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024" "1280x960" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection



Section "ServerLayout"

	Identifier     "Default Layout"
	Screen         "screen1" 0 1
	Screen         "screen0" RightOf "screen1"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	Option "Xinerama" "on"
EndSection


```

---

