---
title: "Hyper-active mouse pointer"
date: 2005-04-13
forum: Desktop Environments
---

### Post by Topper on 2005-04-13
Hi,

I installed Ubuntu and am generally quite pleased with it. However, my mouse pointer moves very, very fast! I've tried setting accelaration and sensitivity all the way down, but it doesn't help at all.

I'm using a touch pad for my hp pavillion ze4500 notebook. Does anyone know how to slow the mouse down?

Regards

---

### Post by heimo on 2005-04-14
You probably have wrong driver for your mouse. Check your /etc/X11/xorg.conf InputDevice section - probably under the InputDevice section for your keyboard. Try using *synaptics* instead of *mouse. *There's also lots of options you can put here to finetune the touchpad (if that driver works for you at all). 

This is from another distribution, but should be helpful:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad]("http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad")

---

### Post by Topper on 2005-04-14
Hmm, I found the xorg.conf file, but I can't edit it, as I'm not root. I'll have to find out how to get write access to the file. 

Anyways, the file contains both a "mouse" entry AND a "Synaptics" entry. PErhaps I should delete the "mouse" entry? I won't use a normal mouse on this laptop...

EDIT:
I changed "mouse" to "synaptics" and I can now control mouse accelleration. Everything is good \\:D/ 

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

```

---

### Post by graigsmith on 2005-05-10
[QUOTE=Topper]Hmm, I found the xorg.conf file, but I can't edit it, as I'm not root. I'll have to find out how to get write access to the file. 

Anyways, the file contains both a "mouse" entry AND a "Synaptics" entry. PErhaps I should delete the "mouse" entry? I won't use a normal mouse on this laptop...

EDIT:
I changed "mouse" to "synaptics" and I can now control mouse accelleration. Everything is good \\:D/ 

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

```[/QUOTE]
 try turning sensitivity all the way up.  you want it to be more sensitive.  that way it moves less when you slightly move the mouse.

---

