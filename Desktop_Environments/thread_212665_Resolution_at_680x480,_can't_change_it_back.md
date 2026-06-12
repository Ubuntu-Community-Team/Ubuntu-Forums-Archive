---
title: "Resolution at 680x480, can't change it back"
date: 2006-07-10
forum: Desktop Environments
---

### Post by AppleNick on 2006-07-10
I just restarted, and Gnome started with a 680x480 resolution (I use 1600x1200). When I go to System -> Preferences -> Screen Resolution, only 680x480 appears on the drop-down menu. What is there for me to do about it?

---

### Post by raldz on 2006-07-10
Did you install or upgrade your graphics driver when this happened?

You could reconfigure back your settings by running this in the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Choad on 2006-07-10
or you could just manually edit /etc/X11/xorg.conf and get to the section describing your monitors screen modes and add in 1024x768 on the 24 bit colour depth section. save it. ctrl+alt+backspace

if x doesnt automatically restart after 5 - 10 seconds login and type startx

---

### Post by handy on 2006-07-10
The bit that looks like this in your /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

