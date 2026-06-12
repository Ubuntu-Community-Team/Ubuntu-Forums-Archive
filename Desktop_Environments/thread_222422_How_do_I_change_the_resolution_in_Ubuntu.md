---
title: "How do I change the resolution in Ubuntu?"
date: 2006-07-25
forum: Desktop Environments
---

### Post by aten on 2006-07-25
Right now I have it at 1024x768 which is the maximum

I need to go higher but there is no area to select.


Thank you.

---

### Post by JoWilly on 2006-07-25
Edit /etc/X11/xorg.conf, look for the screen section with the listed resolutions for each mode.

And add the res you need (i.ex "1280x1024") in front of the others.

---

### Post by aten on 2006-07-25
Thanks alot for the help!

---

### Post by aten on 2006-07-25
> **JoWilly said:**
> Edit /etc/X11/xorg.conf, look for the screen section with the listed resolutions for each mode.

And add the res you need (i.ex "1280x1024") in front of the others.

This is what is says: What am I to change? :-k  :confused: :-k 

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"DELL P780"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```


And it opens as a read only file when I go to the properties of the file it says that I am not the Owner of the file... Sorry that I am such a "n00b" but it's a start:-k

---

### Post by aten on 2006-07-25
Any help, I realy need some help with this.

---

### Post by shawnrgr on 2006-07-30
sudo gedit /etc/X11/xorg.conf

and the resolution you want at the beginning of each modes line.
save and close all windows
press "ctrl+alt+backspace" to restart xserver

---

