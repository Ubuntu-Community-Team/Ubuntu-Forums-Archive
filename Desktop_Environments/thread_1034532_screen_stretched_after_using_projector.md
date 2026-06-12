---
title: "screen stretched after using projector"
date: 2009-01-08
forum: Desktop Environments
---

### Post by emnaki on 2009-01-08
This problem is very annoying. I plugged an Epson projector to my laptop and it stretched my screen. Now with my previous resolution of 1024x768, there is a horizontal stretch such that my firefox icon looks like an ellipse. The problem persists after reboot, where the login screen is fine, but after a few seconds of loading Gnome, the screen is then suddenly stretched. running 
```
dpkg-reconfigure xserver-xorg
```
doesn't help. My xorg.conf is the default one, but I'll post it below anyways:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Please help, thanks!

---

