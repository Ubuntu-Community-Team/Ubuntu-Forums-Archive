---
title: "Enemy Territory resolution problems."
date: 2005-08-16
forum: Gaming &amp; Leisure
---

### Post by SiGNAL748 on 2005-08-16
When I set the resolution in ET to anything less than 1024x768 (i have a crappy integrated graphics, dropping resolution is a must), the game no longer fills the whole screen. Is there a way to make it stretch to fill the entire screen again?  ](*,) 

I think it may have something to do with my desktop resolution being set at 1024x768. I believe that if I set my desktop resolution to whatever resolution I want to play ET in (800x600 for example) it will fill the whole screen. Though this seems like a hassle to be doing everytime I play ET. I'll test if this works tomorrow.

Help, anyone?

---

### Post by installer on 2005-08-17
[QUOTE=SiGNAL748]When I set the resolution in ET to anything less than 1024x768 (i have a crappy integrated graphics, dropping resolution is a must), the game no longer fills the whole screen. Is there a way to make it stretch to fill the entire screen again?  ](*,) 

I think it may have something to do with my desktop resolution being set at 1024x768. I believe that if I set my desktop resolution to whatever resolution I want to play ET in (800x600 for example) it will fill the whole screen. Though this seems like a hassle to be doing everytime I play ET. I'll test if this works tomorrow.

Help, anyone?[/QUOTE]
 Have you just tried adjusting the height and width on your monitor?

---

### Post by Yagisan on 2005-08-18
Check if you have something like this in your xorg.conf
```
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

```If not, et can't change to a lower resolution, that's why it doesn't fill the screen.

---

### Post by SiGNAL748 on 2005-08-18
Where would I find this.... "xorg.conf"  :oops:

---

### Post by DancingSun on 2005-08-18
[QUOTE=SiGNAL748]Where would I find this.... "xorg.conf"  :oops:[/QUOTE]
In "/etc/X11/"

---

### Post by SiGNAL748 on 2005-08-19
```
DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection

```

Looks like you've found my problem. Though now I have a new one. I tried adding the other resolutions in, but it won't let me. I noticed that the file was read-only so I tried going into properties to change it under "Permissions" but I can't. At the bottom it says "You are not the owner, so you can't change these permissions".

How do I go about changing this? 

Thx for the help so far guys!

---

### Post by DancingSun on 2005-08-19
Open up the terminal and type:
```
sudo gedit /etc/X11/xorg.conf
```
You will then be asked for a password, type in your user password.

---

