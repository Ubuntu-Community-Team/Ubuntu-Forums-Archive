---
title: "Samsung Syncmaster 730B"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Das Oracle on 2006-07-17
I have tried searching the forums and google but have been unable to come up with a solution to this problem. My monitor is set to 1280x1024@75. having the res @ 1280x1024 is my preference but the manual recommends I set the refresh rate to 60khz. When I go to change the refresh rate 75khz is all I have as an option. 

here is my xorg.config section:

Section "Monitor"
	Identifier	"SyncMaster"
	HorizSync 30-81
	VertRefresh 50-100
	Option "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
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

---

### Post by aysiu on 2006-07-18
First, press Control-Alt-F1

Log in.

```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can. If you don't know the answer, just go with the default. Then ```
sudo nano /etc/X11/xorg.conf
``` Replace this: ```
Section "Monitor"
Identifier "SyncMaster"
HorizSync 30-81
**VertRefresh 50-100**
Option "DPMS"
EndSection
``` with this ```
Section "Monitor"
Identifier "SyncMaster"
HorizSync 30-81
**VertRefresh 56-75**
Option "DPMS"
EndSection
``` Then save (Control-X, Y, Enter). ```
exit
``` Press Control-Alt-F7 and then Control-Alt-Backspace

---

### Post by VirtuAlex on 2006-07-18
> **Das Oracle said:**
> I have tried searching the forums and google but have been unable to come up with a solution to this problem. My monitor is set to 1280x1024@75. having the res @ 1280x1024 is my preference but the manual recommends I set the refresh rate to 60khz. When I go to change the refresh rate 75khz is all I have as an option.
Do not tell me you are actually doing research to **downgrade** your refresh rate because manual tells you so! Please!!!

---

### Post by Das Oracle on 2006-07-18
downgrade...yeah....except it flickers at higher refresh rates when the res is set to 1280x1024 because the manual said it does that and to set refresh to 60....i provided all the info above and I'm trying the earlier suggestion

---

### Post by Das Oracle on 2006-07-18
I made the change to my vertRefresh and I still do not have the option to change the refresh rate to 60khz. It used to be set to 60khz a while ago but I think one of the updates had made some kind of change and now its not there.

---

### Post by VirtuAlex on 2006-07-18
have you tried dpkg-reconfigure xserver-xorg?

---

### Post by Das Oracle on 2006-07-18
I'm very hesitant to do so because it will mess with all my graphics card configurations wont it?

I just reconfigured xorg and chose the 'advanced' section of the monitor and configured as 30-81 and 56-75, rebooted and no effect

---

### Post by VirtuAlex on 2006-07-18
It is not so scary. Just make a backup ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` I believe it even will do it for you, but just to make sure. If something will go wrong restore it by ```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by Das Oracle on 2006-07-18
please see my edit right above yours...the 'sudo dpkg-reconfigure xserver-xorg did not have any effect.

---

### Post by VirtuAlex on 2006-07-18
what is the graphics card?

---

### Post by Das Oracle on 2006-07-18
nvidia geforce fx 5200 w/ 256Mb....i just reinstalled ubuntu because I've had dapper since 6.02 and some stuff wasn't right...when I use the nv driver i can change the refresh rate to 60 but when I use the nvidia driver the 60khz option goes away....I dont' get it

---

