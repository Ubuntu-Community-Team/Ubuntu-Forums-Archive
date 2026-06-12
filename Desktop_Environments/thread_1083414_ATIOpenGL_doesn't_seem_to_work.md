---
title: "ATI/OpenGL doesn't seem to work"
date: 2009-02-28
forum: Desktop Environments
---

### Post by pan69 on 2009-02-28
Hi.

I have an ATI Radeon 9600 and I'm on 8.10 running Gnome. I currently have my Visual Effect settings set to None because if I enable it I get really bad performance when playing video. Well, I can enable it and tell VLC to render with OpenGL but that shows random black fames during playback.

I lately noticed that the performance of my system is kinda sluggish in that it I can see windows being build up when switching desktops. It didn't used to be like that. It's not really slow but still noticeable. 

For my screensaver I use a blankscreen but the other day I was looking though the different screensavers available and I noticed that rendering them in fullscreen was way to slow. About a year ago, on the same hardware, the previes where really fast and smooth. I have my ATI driver installed and I upgraded it to the latest one just the other day.

This is the content of my xorg.conf and as you can see I have fglrx enabled. Is there something I'm missing? To me it feels like I have no video hardware acceleration at all.

> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
	Option		"VideoOverlay"	"off"
	Option		"OpenGLOverlay"	"off"
EndSection


---

### Post by pan69 on 2009-03-16
OK. I seem to have found the problem. Disabling the ATI hardware acceleration under System > Administration > Hardware Drivers seemed to do the trick. I guess there is some sort of collision with the ATI drivers I had installed.

---

