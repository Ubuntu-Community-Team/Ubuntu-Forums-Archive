---
title: "Stuck at 50hz"
date: 2008-02-01
forum: Desktop Environments
---

### Post by Kaphix on 2008-02-01
I've tried all of the topics I could find on this.

This is my xorg.conf:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Dell"
	Modelname	"Dell E151FP"
	Horizsync	31.0-60.0
	Vertrefresh	56.0-75.0
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@75"
	EndSubSection
EndSection
```

In Screens & Graphics all I can select is 50-53hz@1024x768, and everything is really choppy :(

---

### Post by overdrank on 2008-02-01
> **Kaphix said:**
> I've tried all of the topics I could find on this.

This is my xorg.conf:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Dell"
	Modelname	"Dell E151FP"
	Horizsync	31.0-60.0
	Vertrefresh	56.0-75.0
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@75"
	EndSubSection
EndSection
```

In Screens & Graphics all I can select is 50-53hz@1024x768, and everything is really choppy :(

HI and if you are using the nvidia driver have you tried adjusting the resolution with nvidia settings
```
gksudo nvidia-settings
```

---

### Post by Kaphix on 2008-02-01
It works, thanks. I just got my first ever nvidia card a few days ago, and though its much less of a headache than ATI I don't know anything about it :P thanks for the command though, it has other settings that I was wondering aobut.

---

