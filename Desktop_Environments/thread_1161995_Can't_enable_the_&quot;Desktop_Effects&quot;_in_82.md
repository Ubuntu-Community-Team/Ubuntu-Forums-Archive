---
title: "Can't enable the &quot;Desktop Effects&quot; in 82845G/GL[Brookdale-G]"
date: 2009-05-17
forum: Desktop Environments
---

### Post by arun_3t on 2009-05-17
hi all,

 i have tried compiz-check,followed the intel performance guide and many more but still not able to enable my desktop effects in my system.

My system freezes after enabling the desktop effects to "normal"...

My Graphics Card info:```

Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

My XConf.org
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"intel"
 	Option	"AccelMethod"	"UXA"
	VideoRam	130560
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

If u need anyother details please let me know... any help is appreciated!!!

Advance thanks!!!

---

### Post by andrea000 on 2009-05-18
Intels integrated graphics card 82845 causes problems
in linux.  Common fixes are related to adjusting the
Xorg file there are some work arounds on the net just
google it.

---

