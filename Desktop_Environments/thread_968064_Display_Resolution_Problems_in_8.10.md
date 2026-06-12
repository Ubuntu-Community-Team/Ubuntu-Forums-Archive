---
title: "Display Resolution Problems in 8.10"
date: 2008-11-02
forum: Desktop Environments
---

### Post by Darthape on 2008-11-02
I can't get a display resolution above 800x600 in 8.10. In 8.04 I used the guidance-backends and displayconfig-gtk and in 8.10 since they were not in the intrepid repos I installed them from the hardy repos since ```
sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure -phigh xserver-xorg
xfix 
```
were not working. I have a card that uses the openchrome drivers but that crashes the card and vesa doesn't start x. 
Here is my xorg.conf file
```
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
```

---

