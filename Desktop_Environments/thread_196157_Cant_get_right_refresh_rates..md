---
title: "Cant get right refresh rates."
date: 2006-06-13
forum: Desktop Environments
---

### Post by yellow beard on 2006-06-13
Ive done everything i cant think of but nothing works. Reconfigured x and added my monitors correct refresh rates, added modelines to my xorg.conf but they arnt showing up in my gnome settings. 

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-71
	VertRefresh	50-160
	Modeline "1152x864" 107.48  1152 1208 1336 1584   864  864  867  904
	Modeline "1280x960" 130.05  1280 1352 1512 1800   960  960  963 1003
	Modeline "1024x768" 97.40  1024 1072 1192 1416   768  768  771  809
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960" "1152x864" "1024x768"
	EndSubSection
EndSection
```

Restarting doesnt do anyhing. At the moment i only have the choice of 1024x768,800x600 and 640x480 as my screen size. Ive also tried adding _75 to:  Modes		"1280x960" But that doenst work ither.

---

### Post by Fatjoint on 2006-06-13
[QUOTE=yellow beard]Ive done everything i cant think of but nothing works. Reconfigured x and added my monitors correct refresh rates, added modelines to my xorg.conf but they arnt showing up in my gnome settings. 

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960"
	EndSubSection
EndSection
```
[/quote]

What I've done on my system is remove all the other modes and leave the highest resolution rate you want.  When I've done this I've been able to go to a lower refresh rate if I wanted to, but by default it boots at the only refresh rate available.

---

### Post by yellow beard on 2006-06-14
The thing is, those resolutions dont even show. All i have a choice of is 1024x768, 800 by 600 and 640 by 480. I tried what you said and it gave me the choice of 1280 by 1024 but only a refresh rate of 60 which sucks. I dont know why its not seeing the mode lines i put in.

---

### Post by yellow beard on 2006-06-14
I dont know whats wrong with it. None of the changes i make to xorg.conf work. And if i make one it shits its self and does somthing completley random like changing the log on screen res or adding in a res i dont even want. reconfigureing x doesnt make a difference ither.

---

### Post by yellow beard on 2006-07-11
??

---

