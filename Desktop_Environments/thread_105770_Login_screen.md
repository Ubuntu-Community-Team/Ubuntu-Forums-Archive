---
title: "Login screen"
date: 2005-12-19
forum: Desktop Environments
---

### Post by Maelgwyn on 2005-12-19
When I start my Kubuntu-box, the login screen is in 1280x1024, and my monitor **really** doesn't like that! I get these gross vertical lines everywhere.. Once I've logged in, and am at 1024x768, it's fine..

How do I change the resolution for the login screen???

---

### Post by tkjacobsen on 2005-12-21
You can change that in /etc/X11/xorg.conf in **Section "Screen"**. Just specify the mode to be "1024x768".

Alternatively you can automatically update your xorg.conf:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by sdr_ar on 2005-12-21
This is my "Section Screen" of my xorg.conf:

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"PHILIPS 107T"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

How do I specify 1024x768?
Thanx
Regards
Sergio

---

### Post by veloct on 2005-12-21
The first mode listed is the default so if you wanted to specify 1024x768 as default you would have to change each mode line to look like this:

```
Modes "1024x768" "1280x1024" "1152x864" "800x600" "640x480"
```

restart x, that should do it.

Edit: you could also remove some of the depths (1,4,15) and some of the modes (like I did above) if you like since you are going to edit your xorg.conf.

You can also do this by entering the following:

```
sudo dpkg-reconfigure xorg-xserver
```

This will reconfigure your whole xserver which may be unecessary for what you want to do.

HTH

---

