---
title: "Diplay Settings Stuck/Root?"
date: 2005-04-10
forum: Desktop Environments
---

### Post by kromag on 2005-04-10
Hello all,

Just downloaded Ubuntu and I loaded it on to an addittional hd and everything seemed to take well. I've noticed the diplay is stuck on 640/60 hrtz it makes the screen to big to work with. When I tried to change the resolution, it just high lights the resolution/hrtz numbers and is non-responsive. I have an ATI agp card that works just fine and a 19 inch Mitsu-bitchy monitor.

One other question: accessing root, I don't understand the  the parent/child relationship? I can't log out and go into root like in other distro's. I can how ever access root from a terminal from an user account using my password for the user?! ](*,) 

thanks in advance for any and all help.

kromag

---

### Post by heimo on 2005-04-10
Try ctrl+alt+numberpad's +. That should cycle through different resolutions, but if nothing happens, chances are your xorg.conf file (/etc/X11/xorg.conf) needs to be tweaked. Edit the file ```
sudo gedit /etc/X11/xorg.conf
``` check that in the Screen section you have decent *Modes* line with your desired screen resolution at the beginning of the line. Something like:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
 	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600"
	EndSubSection
EndSection

```

And that the Monitor section has your monitors refresh rate capabilities listed, something like:
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection
```

Examples are from my Nvidia FX 5200 with Hitachi CM752ET (19" CRT) setup.

If that doesn't help, try reconfiguring X, using:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by kromag on 2005-04-16
Nothing worked, as a matter of fact I tried running the live cd version and I was stumped by the very same problems as the other version. I did give it a go though, I spent a few hours a day typing and reading forums and post's. I just didn't see any progress so I stopped. Thank you for all your help, I'll wait till the distros a little less bug free. If I have to work hard just on the visual part of computing it really takes the wind out of my sails.

kromag

---

