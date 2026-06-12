---
title: "ctrl_shift_toggle works invalid"
date: 2005-08-29
forum: Desktop Environments
---

### Post by klim on 2005-08-29
Actually, my problem is fully described here [http://www.mail-archive.com/xfree86@xfree86.org/msg17434.html](http://www.mail-archive.com/xfree86@xfree86.org/msg17434.html). But, unfortunately, nobody answered that thread.

Is there some alternative to ctrl_shift_toggle, something like ctrl_shift_release_toggle? Or is it possible to solve this problem by using xmodmap?

P. S. My xorg.conf keyboard section:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us,ru(winkeys)"
        Option          "XkbOptions"   "grp:ctrl_shift_toggle"
EndSection

---

