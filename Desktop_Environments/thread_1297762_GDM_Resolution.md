---
title: "GDM Resolution"
date: 2009-10-22
forum: Desktop Environments
---

### Post by aobreyss on 2009-10-22
Bonjour,

My display is a LCD television, used 1280*760. Configuration was done using the System/Preferences/Display applet.
GDM uses a lower resolution that I'd like to increase. I'm not sure how to.

xorgconf is relatively empty:

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
	Driver	"fglrx"
EndSection
```

Any assistance 'd be appreciated

---

