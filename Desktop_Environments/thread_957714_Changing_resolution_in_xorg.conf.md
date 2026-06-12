---
title: "Changing resolution in xorg.conf"
date: 2008-10-24
forum: Desktop Environments
---

### Post by Tobywuk on 2008-10-24
Hello, I am trying to change the resolution of two different displays I have. One to be 1280x1020 and the other 1920x1080.

Here is the config file I have:

```

# xorg.conf (X.Org X Window System server configuration file)


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"mac"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option “RenderAccel” “true”

	##This turns on NVidia’s TwinView
	Option “TwinView”
	##Here I’m setting the resolution to the individual monitors.
	Option “MetaModes” “1280×1024 1920×1080&#8243;
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
  	screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

```

Even though I have specified the resolution its still not working. Am I doing something wrong? 

thanks

---

