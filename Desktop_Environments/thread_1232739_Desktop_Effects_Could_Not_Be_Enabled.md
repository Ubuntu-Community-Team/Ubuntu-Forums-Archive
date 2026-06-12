---
title: "Desktop Effects Could Not Be Enabled"
date: 2009-08-05
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2009-08-05
Hi, I recently decided to install the game Alpha Centauri on Ubuntu 9.04. as with having done it before, I added the following code to Xorg to prevent the game from crashing:

```
Section "Extensions"
	Option "Composite" "Disable"
EndSection
```

However, I decided to stop playing the game, and wanted to re-enable my effects, so I went back in to Xorg and deleted the previously mentioned section. However, when I saved, restarted X, and tried to enable the effects, and I get the error "Desktop Effects Could Not Be Enabled". I tried uninstalling and reinstalling the nvidia drivers, but it didn't work either. 

The following is my xorg file: 

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
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

