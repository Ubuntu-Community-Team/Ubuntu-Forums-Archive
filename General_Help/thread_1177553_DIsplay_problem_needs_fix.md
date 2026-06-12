---
title: "DIsplay problem needs fix"
date: 2009-06-03
forum: General Help
---

### Post by DR AMD on 2009-06-03
I already installed Ubuntu 9.04 X64 on my PC...System is working well but display have a bad problems as resolution is 800*600 at maximum and i need to run it at 1024*768...I tried to do that through so many ways but I failed finallly i could do through typing this command on xorg.conf

          SubSection "Display"
		Depth 24
		Virtual	1024 768
	EndSubSection
I dont know what that means but it works up to point as the monitor show only 600*800 of the screen and the rest is hidden and refresh rate still fixed 60 ... I need your help to fix my display resolution and refresh rate ... with concerning that it works fine on other monitors
My  monitor is [ View sonic G70fmb ] and my VGA is [ Via S3g Unichrome Pro IGP ] 
My xorg.conf show after my modification

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth 24
		Virtual	1024 768
	EndSubSection	
EndSection

---

### Post by CatKiller on 2009-06-03
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

According to some promotional material I found by searching for your monitor's model number, the values you're looking for are

```
        HorizSync       30-70
        VertRefresh     50-150

```

---

### Post by DR AMD on 2009-06-03
:KS:KS:KS:KS:KS:KS:KS:KS
IT works well 
Thanks very much for your kind help

---

### Post by ajgreeny on 2009-06-03
Here's an example of my xorg.conf from intrepid which would not detect my monitor correctly.  Jaunty is better and didn't need this edit, but it may help you with your own figures, of course.
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-70
            VertRefresh    50-150
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes       "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
I've left out all the general comments at the top of the text as it will not help your problem.  I hope it helps.

---

