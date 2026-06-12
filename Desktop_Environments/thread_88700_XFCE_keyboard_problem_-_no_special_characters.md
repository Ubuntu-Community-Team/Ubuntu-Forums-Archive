---
title: "XFCE keyboard problem - no special characters"
date: 2005-11-10
forum: Desktop Environments
---

### Post by 23meg on 2005-11-10
In XFCE none of the special characters on my Turkish keyboard seem to work; not just the language-specific characters but everything I should get by pressing with Alt and some I'd get with Shift as well. When I add the keyboard switcher to the XFCE panel I only get one keyboard option, which reads UNKC.

Here's the relevant section of my xorg.conf file
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
	Option		"XkbVariant"	"q"
EndSection
```

This is with XFCE 4.2.2. Any help appreciated; I'm trying to fully transition to XFCE from Gnome and this is a showstopper for me.

---

