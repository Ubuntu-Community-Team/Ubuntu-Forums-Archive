---
title: "Dual Head only working at login screen"
date: 2009-12-24
forum: Desktop Environments
---

### Post by timehAndGod on 2009-12-24
As title; I have configured Dual Head in my xorg.conf, except the moment I login it goes into "Mirror Screens" mode instead of the desired "Dual Head" mode, which only works as desired at the login prompt.

Dump of my xorg.conf file:
```
Section "Monitor"
	Identifier	"Dell"
EndSection

Section "Monitor"
	Identifier	"HP"
	Option		"RightOf" "Dell"
EndSection

Section "Screen"
	Identifier	"Dell Screen"
	Monitor		"Dell"
	Device		"Configured Video Device"
EndSection

Section "Screen"
	Identifier	"HP Screen"
	Monitor		"HP"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"monitor-VGA-0" "Dell"
	Option		"monitor-DVI-0" "HP"
EndSection
```

I'm not too sure what might be causing it, but I have a feeling some session start-up script is over-riding the xorg.conf config on login, but I could be completely wrong...

---

### Post by timehAndGod on 2009-12-24
Well I got this far:
[http://img406.imageshack.us/img406/6264/screenshot1zw.png]("http://img406.imageshack.us/img406/6264/screenshot1zw.png")
I'm just not sure what that distorted section is on the far right. 

The small distorted section on the far right is the only place where windows will not render, but the mouse shows.

With compiz disabled everything is fine.

---

### Post by timehAndGod on 2010-01-06
Still haven't got this working properly. It's either a hardware limitation or a limitation in the xserver-xorg-driver-ati package.

Anyone else got anymore information? Metacity is kinda lame.

---

### Post by timehAndGod on 2010-01-17
These forums need a 'bump' button...

Anyway, the issue still stands. It's either a hardware issue, or a driver limitation. This is where I am hoping someone else can fill me (and potentially others) in.

---

