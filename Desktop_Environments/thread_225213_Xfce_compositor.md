---
title: "Xfce compositor"
date: 2006-07-29
forum: Desktop Environments
---

### Post by NicePics13 on 2006-07-29
I'm using Xfce with the composite manager and I must say it looks good and is relatively fast (good fps even in 3D) after replacing the Radeon OSS driver with one from [http://xgl.compiz.info/](http://xgl.compiz.info/) - now there's even direct rendering!

My problem is after a while everything starts lagging and slowing down. Like some graphics buffer has filled up or something :-k  Don't know... Usually after using Thunar jerkiness sets in.

Is there some buffer purge option I could add to the device section in xorg.conf? I have a 9600pro 128MB card.

```
Section "Device"
	Identifier	"Radeon9600"
	Driver		"radeon"
	BusID		"PCI:2:0:0"
	Option		"RenderAccel"	"true"
EndSection
```

Thanks :)

---

