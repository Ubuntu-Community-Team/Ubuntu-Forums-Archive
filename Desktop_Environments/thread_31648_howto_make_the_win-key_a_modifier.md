---
title: "howto make the win-key a modifier ?"
date: 2005-05-04
forum: Desktop Environments
---

### Post by odix on 2005-05-04
I want to have the win-key as a modifier (e.g. for key combinations like win+F1, etc), what shall I do ?

odiX

---

### Post by Leif on 2005-05-04
System->Preferences->Keyboard shortcuts. Click on what you want to do and enter the combination.

---

### Post by odix on 2005-05-04
Thank you, I know this, but ...

I'm using german keyboard layout, and the win-key doesn't act like a modifier key (like the Alt key or Shift key).

regards

---

### Post by odix on 2005-05-04
Hi,
I've managed myself :-)
For system wide configuration I have changed /etc/X11/xorg.conf, the keyboard section now looks like this:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"nodeadkeys,altwin:meta_win,lv3:ralt_switch"
EndSection

```

regards odiX

---

