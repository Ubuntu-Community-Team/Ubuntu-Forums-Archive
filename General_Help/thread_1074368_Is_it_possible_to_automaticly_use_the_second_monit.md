---
title: "Is it possible to automaticly use the second monitor only?"
date: 2009-02-19
forum: General Help
---

### Post by hlverstoep on 2009-02-19
Hi,

I have a laptop with an ATI card (X1400). I bought a second monitor to connect via the VGA output. Because the two monitors together (1680x1050(external) and 1280x800(laptop)) are larger than the maximum 3D accelaration area (2048x2048) and I'm using compiz, I would like to use the external monitor only.

The problem I now have is that I cannot get the external monitor to be the default monitor used on startup, using the open-source ati drivers. The fglrx driver is able to do this, but in that case I have other problems with video playback (I have to turn compiz off, to make sure X doesn't crash when playing a video).

I hope someone has an answer to this problem, preferably using the open-source driver.

hlverstoep

---

### Post by hlverstoep on 2009-03-13
Solved it (finally) by using the radeon driver 6.11.0 package from jaunty and the following xorg.conf, I hope this can help somebody else. 

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
	Option		"AccelMethod" "EXA"
EndSection

Section "Monitor"
	Identifier	"LVDS"
	Option		"Disable" "true"
EndSection

Section "Monitor"
	Identifier	"Default Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Default Monitor"
	Device		"Configured Video Device"
	SubSection	"Display"
		Virtual	1680 1050
	EndSubSection
EndSection
```

---

