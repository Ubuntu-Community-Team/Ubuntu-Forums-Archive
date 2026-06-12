---
title: "Non-Gnome apps and greek stressed vowels"
date: 2006-04-05
forum: Desktop Environments
---

### Post by ksenos on 2006-04-05
Greetings to all.

I have a problem for several months now and I still haven't figured out how to solve it.

I use Ubuntu 5.10 and everything about greek works flawlessly in gnome applications. In non-gnome apps, although I can input greek text, I cannot input stressed vowels like "&#940;,&#972;,&#941;,&#943;,&#971;". The non-gnome apps include a few kde apps like amarok, k3b and quanta, and also win32 apps that run using wine. 

My xorg.conf keyboard configuration is this:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,el"
	Option		"XkbOptions"	"grp:alt_shift_toggle"
EndSection
```

Any suggestions? Thanks in advance.

---

