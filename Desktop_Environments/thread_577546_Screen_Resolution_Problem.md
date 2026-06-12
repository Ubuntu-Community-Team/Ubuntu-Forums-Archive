---
title: "Screen Resolution Problem"
date: 2007-10-16
forum: Desktop Environments
---

### Post by chandrakant11 on 2007-10-16
Hello 
I have Install ubuntu 6.10 and P4 , 512 , Intel Board.

Screen Resolution show
 1280x1024 @6oHz ,  
 1024 X 768 @ 85Hz.
 800 x 600 @ 85Htz
 640 x 480 @ 85 Htz
 
 What should I so If I have to Select Resolution between  1280x1024 @6oHz  AND  1024 X 768 @ 85Hz.

 Means How can I have more Selection of Modes in Screen Resolution ..  
 Where should I make changes . I have attached xorg.conf 
 Thank

---

### Post by Wiebelhaus on 2007-10-16
> sudo dpkg-reconfigure -phigh xserver-xorg

Runs this command and you'll then be able to select multiple resolutions , good luck mate.

---

### Post by trorion on 2007-10-16
Alternatively you can add resolutions to your xorg.conf (must be root/sudo) under this section (you need to add it to whichever color depth you are using; likely 24:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"700B"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

---

