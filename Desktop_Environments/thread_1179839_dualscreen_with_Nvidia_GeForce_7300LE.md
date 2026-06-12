---
title: "dualscreen with Nvidia GeForce 7300LE"
date: 2009-06-06
forum: Desktop Environments
---

### Post by kalesh7 on 2009-06-06
Hi all,
I need help with setting up dualscreens, it works in windows (XP) but I am a bit lost with ubuntu.

Here is my xorg.conf (I know I haven't made much changes yet, but I don't know what changes to make)
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option "RenderAccel" "True"
	Option "TwinView"
	Option "MetaModes" "1280×1024 1280×1024"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

stuff about my setup
card: Nvidia GeForce 7300 LE

screen 1 (primary):
    name: Daewoo S719BF
    resolution: 1024x768
    refresh: 60Hz

screen 2:
    name: HDTV
    resolution: 720x480
    refresh: 60 Hz
    connector: Component High Defenition Televisions
    signal: 480i SDTV

Note: the TV is not a HDTV but that is the setup that works on windows.

---

