---
title: "How do you change display resolution (monitor; 800X600)"
date: 2006-01-11
forum: Desktop Environments
---

### Post by cowboy_jim44 on 2006-01-11
How do I change the resolution on the monitor?

---

### Post by Pixel on 2006-01-11
[QUOTE=cowboy_jim44]How do I change the resolution on the monitor?[/QUOTE]
you can go to Gnome Menu -> System -> Preferences -> Screen Resolution

Or open up your xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

Find the line where it says something like this...

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Monitor		"Sceptre"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
```

Choose whatever color depth you want then just add/remove the right resolutions...

Be careful though, if you make any typos in there your X probbably wont start, I only reccomend doing this if your possible resolution isn't listen in the gnome preferences.

---

### Post by 23meg on 2006-01-11
Take a look at the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=83973").

---

