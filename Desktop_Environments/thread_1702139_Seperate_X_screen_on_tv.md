---
title: "Seperate X screen on tv"
date: 2011-03-07
forum: Desktop Environments
---

### Post by sokekoke on 2011-03-07
I can't get separate x screen to work!

I'm running ubuntu 10.10 on an ASUS UL80VT with a GeForce G210M.

When i connect the laptop to my tv, with a hdmi cable, i get TwinView running with no problem using the "nvidia x server settings" gui. The mouse sensitivity gets a little weird, and i get some horizontal screen flicker when i watch movies (compiz disabled and all). But when i try enable "separate X screen" i get the "apply whats possible" box, and then my tv stays black :-(

here is my /etc/xorg.conf

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

