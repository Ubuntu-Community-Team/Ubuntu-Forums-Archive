---
title: "Gnome Settings Daemon Restarted Too Many Times"
date: 2009-01-16
forum: Desktop Environments
---

### Post by KennethGodwin on 2009-01-16
After changing my xorg.conf to the following (just adding the SubSection in bold):

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
[b]        
        SubSection "Display"
             Depth 24
             Modes "1920x1200" "1440x900"
             Virtual 3360 2100
        EndSubSection
[/b]
EndSection


When I boot into Gnome, I get the message the Gnome Settings Daemon Restarted Too Many Times due to Bus Timeout. It works fine...except for the fact all the settings information (e.g. themes, background) is gone. Which is annoying...

If I try loading up KDE instead...it'll white screen and lockup. 

So I'm running XFCE atm, which works perfectly fine...but I prefer Gnome. ;)

---

