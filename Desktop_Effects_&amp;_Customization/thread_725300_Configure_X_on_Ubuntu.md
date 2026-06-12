---
title: "Configure X on Ubuntu"
date: 2008-03-15
forum: Desktop Effects &amp; Customization
---

### Post by ubuntoexpert on 2008-03-15
How do I modify the X-settings from a terminal in Ubuntu.
I modified these settings, and can not find out how ignore these and return to the previous settings. Is that possible?
Can I find some default settings somewhere?

---

### Post by benerivo on 2008-03-15
You can view and edit the settings with```
sudo nano /etc/X11/xorg.conf
```and you can reconfigure them with ```
sudo dpkg-reconfigure xserver-xorg
```and a really basic xorg.conf file would look something like this (105 key keyboard with a GB layout). If you have a nvidia card, I know you can use "nv" instead of "vesa", and if  you have installed the restricted nvidia driver then use "nvidia".```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver	"kbd"
	Option	"XkbRules"	"xorg"
	Option	"XkbModel"	"pc105"
	Option	"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver	"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor	"Configured Monitor"
EndSection
```

---

### Post by overdrank on 2008-03-15
> **ubuntoexpert said:**
> How do I modify the X-settings from a terminal in Ubuntu.
I modified these settings, and can not find out how ignore these and return to the previous settings. Is that possible?
Can I find some default settings somewhere?

HI and if you would like to reconfigure you xorg then you can use this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If you would like to edit the xorg from the terminal then you can use nano of vi
```
sudo nano /etc/X11/xorg.conf
or
sudo vi /etc/X11/xorg.conf


```
Edit to slow lol :)

---

