---
title: "graphic error while using firefox"
date: 2009-05-11
forum: General Help
---

### Post by SpinningAround on 2009-05-11
I have notice a strange graphic error when using firefox since I updated from ubuntu 8.10 (64bit) to 9.04 (64bit), I don't have compiz activated so don't think the problem is there. I'm using a Ati Radeon HD 4670 card, the monitor is a Samsung Syncmaster 2233BW
xorg.conf
```

Section "Monitor"
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
EndSection


```

I uploaded a screenshoot on the graphic error, the black isn't suppose to be there :P screenshoot from this site [http://www.prisjakt.nu](http://www.prisjakt.nu)

---

