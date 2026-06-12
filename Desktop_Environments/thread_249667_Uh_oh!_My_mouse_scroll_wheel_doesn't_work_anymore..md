---
title: "Uh oh! My mouse scroll wheel doesn't work anymore."
date: 2006-09-02
forum: Desktop Environments
---

### Post by solarwind on 2006-09-02
Hi all,

I just noticed (maybe 2 hours ago) that after installing my fglrx drivers for my ati x300, my mouse scroll wheel doesn't work anymore!

It worked fine before I installed the ATI drivers, but now I cant scroll using the mouse.

What could be the cause?

---

### Post by croak77 on 2006-09-02
Check your /etc/X11/xorg.conf and look for a line called;

"ZAxisMapping"   "4 5"

Make sure it's un-commented (remove the '#' before it). If it's not there add it under your mouse options.

---

### Post by Anduu on 2006-09-03
Yep...when the ATI drivers were installed your xorg.conf was modified.

Lokk for the mouse section...it should look something like this

```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection
```

---

