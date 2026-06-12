---
title: "really weird widescreen problem"
date: 2007-03-31
forum: Desktop Environments
---

### Post by fatinbox on 2007-03-31
Hi there,

I'm a really-really green newcomer to ubuntu; played with various distros for the past month or so, and finally decided on edgy to replace my ever-slower, patchy, and horrific WinXP.

Overall a nice experience (50 secs boot time vs 3.5 minutes, just to give an example), but I ran into 3 big problems I can't get around: Ubuntu can't see widescreen, sound drivers, wireless card. This post is about the first one, and I'll get to the others time permitting. Help is really appreciated. 

_**To the point**_: I have a Gateway 3040GZ laptop; max resolution is 1280 x 768 (i think), but I'm getting an annoying 1024x768 that makes my friends' pictures look freaky, among other unpleasantries. I read all the posts on the matter, and they all say "go to xorg.conf and change it". And here's the **_weird_** part for me: nowhere in my xorg.conf does it say anything about 1024. Here's actually what I have in the "screen" section.


Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection

Help, anyone ? I really don't want to go back to "windows and gates".

---

