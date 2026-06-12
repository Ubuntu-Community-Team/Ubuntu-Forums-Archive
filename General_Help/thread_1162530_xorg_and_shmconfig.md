---
title: "xorg and shmconfig"
date: 2009-05-17
forum: General Help
---

### Post by fontenot_1031 on 2009-05-17
I'm trying to turn off my touchpad and to use gsynaptics I know I have to set SHMConfig to true under input devices. The only problem is in my xorg.conf there never was an input section for mice.
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
	Load	"dbe"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

Can anyone tell me where I can set SHMConfig in my xorg.conf?

---

