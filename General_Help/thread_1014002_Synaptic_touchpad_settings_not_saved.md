---
title: "Synaptic touchpad settings not saved"
date: 2008-12-17
forum: General Help
---

### Post by Farenji on 2008-12-17
Hi,

I have a Dell Inspiron 640M laptop with a default install of ubuntu 8.10. It has a touchpad using the synaptics driver. To be able to change the config of the touchpad, I have to add 'Option "SHMConfig" "true"' in my xorg.conf. So far so good. This has worked like a charm since 7.04.

I've noticed that since a while (not sure how long exactly) the synaptics touchpad settings are not saved permanently. They are saved during the same X session. But after a reboot or a X restart, the settings are back to the default. I always like to disable tapping but now I have to do this every time, cause every time I restart tapping is on again.

I checked my logfiles for clues or error/warning messages but I cant find any and I dont know where else to look for the cause or a solution. Anyone experiencing the same issue?

---

### Post by Farenji on 2008-12-21
Anybody?

---

### Post by 2hot6ft2 on 2008-12-21
This thread is all about the touchpad but it didn't work for me. [http://ubuntuforums.org/showthread.php?t=271052](http://ubuntuforums.org/showthread.php?t=271052)

Have you tried going to System>Preferences>Mouse and on the touchpad tab set it to disable. Then go to System>Preferences>Sessions and on the third tab Session Options click on Remember Currently Running Applications.

I don't know if it will work or not but it may. Of course it will completely disable the touchpad not just the tap.

---

### Post by fondueknights on 2009-02-10
I had the exact same problem on my Dell and was able to fix it.

First, I installed gsynaptics and altered xorg.conf.

Here is what my InputDevice section looks like:

```
Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver 		"synaptics"
	Option 		"SendCoreEvents" 	"true"
	Option 		"Device" 		"/dev/psaux"
	Option 		"Protocol" 		"auto-dev"
	Option 		"HorizScrollDelta" 	"0"
	Option 		"SHMConfig" 		"on"
EndSection
```

I had to add in this section to get things working properly:

```
Section "Serverlayout"
	Identifier 	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Once I did that, tap to click stayed off for good! Hope it works for you.

---

