---
title: "keyboard layout"
date: 2007-12-14
forum: Desktop Environments
---

### Post by hirohitosan on 2007-12-14
Hi there. I try to install additional keyboard layout. I tried manually and I modify the file xorg.conf and now looks like this

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,ro"
#	Option          "XkbLayout"     "ro"
	Option          "XkbOptions"    "lv3:lwin_switch"
```

I add a keyboard switcher at the panel. The switcher works but it doesn't switch the k. layout. I mean I can't use ro k.l. in any text editors

thanks !

---

