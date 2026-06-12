---
title: "ATI radeon X1200 questions.."
date: 2009-04-02
forum: General Help
---

### Post by iu34 on 2009-04-02
When I go under "Screen Resolution", on the pseudo-monitor, it says "unknown", my max screen resolution is 1280*800, and the only refresh rate is 60hz. Is there any way to have a bigger resolution?

I recently installed the x1250 driver from ati's support page, after searching around and hearing that it helps. Also, if I don't enable the fglrx driver, the screen on here goes crazy with lines all over the screen.

this is all that's in my xorg.conf (except for the explanation at the beginning)
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
	Option		"UseFBDev"		"true"
	Driver	"fglrx"
EndSection

```

---

