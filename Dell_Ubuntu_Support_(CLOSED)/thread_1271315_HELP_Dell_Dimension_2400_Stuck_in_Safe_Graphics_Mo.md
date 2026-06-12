---
title: "HELP Dell Dimension 2400 Stuck in Safe Graphics Mode aka Vesa"
date: 2009-09-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hellzkeeper1216 on 2009-09-20
I am stuck with a 600x800 display. I can't seem to edit my xorg.config I'll post the output of the default maybe someone can explain to me or help me get out of this!?! Please any help would be greatly appreciated!

```
# xorg.conf (X.Org X Window System server configuration file)

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Monitor	   "Configured Monitor"
    Device	   "Configured Video Device"
EndSection
```

I am finding it increasingly difficult to do any homework or much of anything with it in this current state please help!

---

