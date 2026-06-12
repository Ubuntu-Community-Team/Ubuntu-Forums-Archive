---
title: "issues with xorg, please help"
date: 2007-04-26
forum: Desktop Environments
---

### Post by Locuss on 2007-04-26
I know this should probably be dealt with by the x.org people, but the ubuntuforums people are a lot nicer.

Right now, I have a 27" flatscreen, widescreen lcd Norcent panel. It has a vga plug in it, and before a very long series of mishaps, worked perfectly with kubuntu 6.10. Even after upgrading to feisty, no problems. Then my mishaps, and my own mistakes(I at least admit they were my own) and now, I'm stuck.

Basically, X now will not start. I tried to fix problems with my scrollwheel, and x then started to fail to work on the widescreen. Basically, I think the hertz is too high. 

First, I need some help with the monitor section from xorg.conf 
```

Section "Monitor"
	Identifier	"hp f1503"
	Option		"DPMS"
EndSection
```

What do I change here?

and this is my screen section

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"hp f1503"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

I saw somewhere that X -configure would help me, from the console login. I tried that, but one thing, how do I get OUT of X -configure, or set options? All I get is a grey screen, the basic cursor displayed and working.

---

### Post by hellblade on 2007-04-28
Can you post your "/var/log/Xorg.0.log"?

Also after backing up your "/etc/X11/xorg.conf" try this command: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
which will recreate your xorg.conf

---

