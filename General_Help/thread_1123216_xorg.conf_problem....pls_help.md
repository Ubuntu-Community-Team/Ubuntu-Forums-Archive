---
title: "xorg.conf problem....pls help"
date: 2009-04-11
forum: General Help
---

### Post by vajeen on 2009-04-11
I wanned to change the login window resolution to 1125x864 (it was set to higher resolution)
so i opened the xorg.conf file (/etc/X11/xorg.conf) and it gave me this...

----------------------------------------------------------------------------


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
--------------------------------------------------------------------------
how can i change the resolution???????
pls help........

---

