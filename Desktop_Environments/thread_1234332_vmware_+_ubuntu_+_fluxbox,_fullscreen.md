---
title: "vmware + ubuntu + fluxbox, fullscreen?"
date: 2009-08-07
forum: Desktop Environments
---

### Post by Diabolis on 2009-08-07
I have a virtual machine that initially had gnome, but I removed it and now I'm using Fluxbox. The problem is that when I go to full screen mode, the desktop remains at 800x600 with a wide black border surrounding it. Anyone know how to make Fluxbox go full screen?

---

### Post by flux_user on 2009-08-21
> **Diabolis said:**
> I have a virtual machine that initially had gnome, but I removed it and now I'm using Fluxbox. The problem is that when I go to full screen mode, the desktop remains at 800x600 with a wide black border surrounding it. Anyone know how to make Fluxbox go full screen?

Ok... Your question is confusing; please  do not take offense.  Your question can be interpreted in several ways;

[LIST]
[*]Changing the  resolution of flubox in your virtual environment so that is full screen.
[*]Have the  virutal environment go full screen on your current desktop.
[*]Changing the  host environment on your machine to occupy full screen.
[/LIST]

You might want to try and:
[LIST=1]
[*]Re-pharase your question
[*]Provide a screenshot showing what you mean.  Screen shot with arrows being draw into the pic.
[/LIST]

---

### Post by Diabolis on 2009-10-02
Found the solution:

```
sudo vim /etc/X11/xorg.conf
```

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver "vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Subsection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection

```

The important part is to use **vesa** instead of the **vmware** driver.

---

