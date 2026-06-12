---
title: "GeForce MX440 doesnt save settings"
date: 2009-05-14
forum: General Help
---

### Post by bolter40k on 2009-05-14
I am running 9.04.  I have an Envision 710e monitor.  Im using a GeForce MX 440 video card in an old gateway.  

I have the drivers installed properly and everything looks and works fine.  

When i boot to ubuntu its in the resolution 1024x768 but my monitor is able to go to 1152x864.  I set it to 1152x864 and apply.  Then when i turn my computer back on to use it it goes back to the 1024x768. how can i make the driver save the settings.  I tried clicking save settings to X Configuration File but i get    Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Please help this is very annoying to have to set the resolution over and over again

Here are the contents of my xorg config file if it is relevant

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

---

### Post by Elfy on 2009-05-14
If you get the error while running nvidia-settings - run it as root from a terminal

```
gksudo nvidia-settings
```

---

