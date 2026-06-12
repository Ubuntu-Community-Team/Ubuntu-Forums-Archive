---
title: "E520 N Display Question"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by ScottLij on 2007-06-12
I just got my new E520 N with the NVIDIA card and I installed the "unsupported driver".  I was just wondering if it's possible to rotate the display 90 degrees as my monitor has the capability to rotate.

---

### Post by benanzo on 2007-06-12
Have tried the option in the **System -> Preferences -> Screen Resolution** menu?  If that doesn't work, I think there is an option in the **nvidia-settings** menu.
```
gksu nvidia-settings
```

---

### Post by ScottLij on 2007-06-12
In System -> Preferences -> Screen Resolution the option to rotate the screen is grayed out and I don't see an option to rotate the screen in the window that appears when I type gksu nvidia-settings.  Is there something I have to do to enable that option?

---

### Post by ScottLij on 2007-06-12
I just noticed that in the gksu nvidia-settings window that my display is listed as a CRT-0.  Could this be the problem?  How do I tell it that it's a LCD thats capable of rotation?

---

### Post by ScottLij on 2007-06-13
I figured it out by searching around.  I had to change the /etc/X11/xorg.conf file to contain a line that says 

```
Option          "RandRRotation" "on"
```

So this is what that section of the file looks like when complete:

```
Section "Device"
	Identifier	"nVidia Corporation GeForce 7300 LE"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option          "RandRRotation" "on"
EndSection
```

---

