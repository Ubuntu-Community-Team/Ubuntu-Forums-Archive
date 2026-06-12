---
title: "Switching Xfce Keyboard Layouts"
date: 2008-02-18
forum: Desktop Environments
---

### Post by vasiliymeshko on 2008-02-18
I'm trying to add a keyboard layout to XFCE (Ukrainian Phonetic). My issue is that even though I have added the layout under keyboard options, I can't seem to get it to switch under keyboard layout switcher applet. Clicking on it seems to have no effect at all, and it just stays on US.

---

### Post by vasiliymeshko on 2008-02-18
I've made the following changes to xorg.conf:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"macintosh"
	Option		"XkbLayout"	"us,ua"
EndSection


```

Unfortunately, this only enables the regular Ukrainian layout. What do I do to get phonetic?

---

