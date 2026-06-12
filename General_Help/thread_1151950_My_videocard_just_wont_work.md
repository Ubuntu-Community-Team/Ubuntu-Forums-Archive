---
title: "My videocard just wont work"
date: 2009-05-07
forum: General Help
---

### Post by Thanatios on 2009-05-07
Greetings!

Not long ago I installed Ubuntu on my desktop. Now I have 2 videocards:
> 00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
01:09.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

I have 2 monitors, both pluged in. 

My Xorg.conf:

> Section "Device"
	Identifier	"0 Configured Video Device"
	Option		"UseFBDev"		"true"
 	Screen      0
	Driver        "i810"
	BusID        "PCI:0:1:0"
	Option "DDCMode" "True"
	Option "MonitorLayout" "CRT,CRT"
EndSection

Section "Device"
	Identifier	"1 Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver       	 "nv"
	BusID        	"PCI:1:2:0"
 	Screen      1
	Option "DDCMode" "True"
	Option "MonitorLayout" "CRT,CRT"
EndSection

Section "Monitor"
	Identifier	"0 Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"1 Configured Monitor"
EndSection

Section "Screen"
	Identifier	"0 Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Screen"
	Identifier	"1 Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen      0  "0 Default Screen"
    Screen      1  "1 Default Screen" RightOf "0 Default Screen"
    Option	 "Xinerama" "true"
EndSection

Now my error is very strange, every time I boot up, I get:

> No devices detected

And after clicking OK I get:

> There already appears to be an X server running on display :0 etc etc

I right now am using my nvidia videocard. And my second screen wont even blink. Its off all the time.

I have been frustrating over this for about 2 days now.
Anybody willing to help me?

Thanks in advance!

---

### Post by Thanatios on 2009-05-07
bumperthebump?

---

