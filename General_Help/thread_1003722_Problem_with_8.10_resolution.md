---
title: "Problem with 8.10 resolution"
date: 2008-12-06
forum: General Help
---

### Post by zay2 on 2008-12-06
Hello!

I upgraded from 8.04 kde 3.5.9 to 8.1.0 and kde 4.1. 

at first i only had 800x600 resolution, but after installing recommended nvidia drivers i could set my screen to 1024x768, but not higher...

i tried tempering with xorg.conf entering Modes like "1280x1024" "1024x768" there, but xserver would not start any more and when i tried running it from command prompt, it said, that modes was wrong keyword (or something) for that section... or something similar.

In any case. My goal is to get my screen back to 1280x1024 resolution. Please help me!

Edit: I searched the web abit and i could edit xorg.conf enought to get xserver running again, but the outcome was not the best. Resolution could have been 1280x1024, but everything was off the screen towerds upper-left corner for about 200-300 pixels and monitors auto adjustment did nothing.

I added this in "Screen section"

SubSection "Display"
depth 24
Virtual 1280 1024
Modes "1280x1024"
EndSubSection

---

### Post by zay2 on 2008-12-06
update:

i changed this : 

SubSection "Display"
depth 24
Virtual 1280 1024
Modes "1280x1024"
EndSubSection 

for
SubSection "Display"
depth 24
Modes "1280x1024"
EndSubSection 

The screen is positioned correctly now, but the resolution is not 1280x1024 and i cant reset it to that....

Still need help!

---

### Post by utnubuuser on 2008-12-06
Did you try > sudo dpkg-reconfigure xorg-xserver

This thread > [http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

and this > [http://answers.yahoo.com/question/index?qid=20080910220229AAdakeP](http://answers.yahoo.com/question/index?qid=20080910220229AAdakeP)

There is also a similar command for reconfiguring nvidia driver, but I can't find it at the moment,  - if I find it, I'll post it.

---

### Post by zay2 on 2008-12-06
either im too dumb to understand those texts usefulness or they arent all that useful... to me anyway.

As i understood, there was something about program, that forces screen to use better resolutions?

Why does it have to be forced? It all worked fine with kde3.5.9...

i have working drivers and editing xorg.conf to include 1280x1024 resolution does not seem to work... when i go under the display settings i noticed that the display rate is also only 50, while it should he 60 or 75.

---

### Post by utnubuuser on 2008-12-06
A  question:  If it all worked fine,  why the upgrade?  Better features?  Help testing?

---

### Post by zay2 on 2008-12-06
Hehe well. 

I needed to do some work and i use my linux computer for it. When i stared it i got some kind of IceAuthority error that i already have encountered, when i installed kubuntu for my mother... in any case, trying to fix that on moms comp ended up in 8 hours of wasted time so i just reinstalled 8.04... since it offered upgrade i thought - what the hell, i need to install all the programs anyway, so why not try kde4.1....

so thats my story... I have small update though.. i edited xorg conf more and added some text from the thread you gave me and my xorg.conf looks like this now :

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth 1
		Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

the maximum resolution i get is only 1152x864 though. :cry:

---

### Post by zay2 on 2008-12-06
any ideas, anybody?

---

