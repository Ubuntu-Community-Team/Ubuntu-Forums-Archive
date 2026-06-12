---
title: "Lost the screen resolution on Aer AL1702W"
date: 2009-06-13
forum: General Help
---

### Post by ptsubin on 2009-06-13
I have installed Ubuntu 9.04 on Desktop PC. Every thing went fine, even compiz. After two days i turned on the system, i saw the resolution was changed, and display settings does not detect Acer Monitor, but it was fine the day before. I tried xresprobe. it gives me following output,

root@edpc:/home/embedded# xresprobe xserver-xorg-intel
id: Acer AL1702W
res: 1440x1440 1440x900 1280x1024 1152x864 1024x768 832x624 800x600 720x400 640x480
freq: 30-83 55-75
disptype: 

And please tell me how can i put these info to my xorg.conf and make it look nice, now my xorg.conf is:

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

It looks same for my laptop also, but where can I put information that it should use xserver-xorg-intel and the vendor and all, i am just afraid to play with X, there are rumors that wrong settings can damage the video card.. Help me..

---

