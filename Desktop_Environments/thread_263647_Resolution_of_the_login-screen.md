---
title: "Resolution of the login-screen"
date: 2006-09-23
forum: Desktop Environments
---

### Post by dupa on 2006-09-23
When i installed Ubuntu, it set at 2048x the resolution of my screen when my monitor just support up to 1600x1200, luckily my monitor has not dead fr it, but I suggest to the developer to change the default setting of the resolution to a more "safe" value.

after logging in, I manually changed the resolution for my user to 1024x768, using the GUI administration tool.

but the resolution of login screen remained at 2048.. so I manually edited the /etc/X11/xorg.conf file to just support up to 1024x768 resolutions. (I think that is a good idea to put in the distribution a GUI tool to do that job... i looked for a GUI tool for it in the distro, but didn't find it)

But I have still a problem.

When I reach the login screen the MONITOR resolution is at 1024x768, but the DESKTOP size is larger! so i had to scroll around the desktop to fully view it.

How can i set also the desktop size of the login screen to be at 1024x768?

Thank you!

---

### Post by powder on 2006-09-23
I had to add a custom modeline to my xorg.conf to fix this problem.  You can generate a modeline here:

[http://www.dkfz-heidelberg.de/spec/linux/modeline/](http://www.dkfz-heidelberg.de/spec/linux/modeline/)

Then add this modeline to your xorg.conf in the "monitor" section.  Mine looks like this:

```
Section "Monitor"
	Identifier  "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	HorizSync    30.0 - 96.0
	VertRefresh  50.0 - 160.0
	# V-freq: 85.00 Hz  // h-freq: 85.99 KHz
	Modeline    "1280x960" 167.84  1280 1368 1576 1952   960  960  963 1011 -hsync +vsync
EndSection
```

---

### Post by dupa on 2006-09-23
> **powder said:**
> I had to add a custom modeline to my xorg.conf to fix this problem.  You can generate a modeline here:

[http://www.dkfz-heidelberg.de/spec/linux/modeline/](http://www.dkfz-heidelberg.de/spec/linux/modeline/)

Then add this modeline to your xorg.conf in the "monitor" section.  Mine looks like this:

```
Section "Monitor"
	Identifier  "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	HorizSync    30.0 - 96.0
	VertRefresh  50.0 - 160.0
	# V-freq: 85.00 Hz  // h-freq: 85.99 KHz
	Modeline    "1280x960" 167.84  1280 1368 1576 1952   960  960  963 1011 -hsync +vsync
EndSection
```

I have not problems with the Monitor resolution. It is ok at 1024x768.

My problem is that the desktop (at the login mask) is larger than my desktop.
I want that both the destop and the monitor should be at 1024x768.

---

### Post by theToolman on 2006-09-26
I am also looking for a solution to this.  I have intentionally made a custom modeline, and I have the same problem.  The screen is correctly placed at 1270x958 but the X server is using a 1280x1024 and so panning and scanning via the mouse.

I am doing something a bit funky tho.  I have mounted a 17" lcd panel in a 17" CRT case (apple studio pro monitor case with a mini ITX :).  The difference in screen measurement between the crt and lcd mean I want to run in a slightly lower X resolution while still sending a full signal - generating black overscan borders :)  

```
Modeline        "apple"  135.00         1270 1287 1431 1688   958 985 988 1066 +hsync +vsync
```

---

### Post by theToolman on 2006-09-26
Ended up having to add a "virtual" line into the display section, and get my resolution to a multiple of 8.

```
        SubSection "Display"
                Depth           24
                Modes           "1272x960@60" "1280x1024"
                Virtual 1272 960
        EndSubSection

```

it seems to be defaulting to using a virtual res of 1280x1024 even tho the modeline gives the resolution.

---

