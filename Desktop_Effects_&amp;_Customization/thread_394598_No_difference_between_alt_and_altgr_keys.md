---
title: "No difference between alt and altgr keys"
date: 2007-03-27
forum: Desktop Effects &amp; Customization
---

### Post by majo83 on 2007-03-27
Hi there,
I have the problem that under gnome and X in general no difference between the alt and the altgr key exists. I therefore can't use symols like at or pipe. Under the normal text-console with no X everything works perfect.

Also notable are the following phenomena:
1) If I press ctrl and alt and e.g. f1 I can't switch to the console
2) If I try showkey under a normal gnome-terminal I get the message "Could not get a file descriptor for the console" (even if I try as root)
3) If I stop gdm and make xinit to get only a bare xterm showkey scrolls down the xterm without output. It doesn't end after 10 seconds of no key-input

Here is the relevant snipped from /etc/X11/xconf.org
---
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"  
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de-latin1.map.gz"
	Option 		"Variant"   	"nodeadkeys"
EndSection
---
Can anybody help?

Thanks and Greetings from Ulm, Germany
majo83

---

### Post by 1/0 on 2007-03-27
Check the keycode with xev. (Mine is 113.) Maybe this will help:

```
echo "keycode 113 = Mode_switch" >> ~/.Xmodmap
```

Otherwise you might want to switch to an international pc105.

---

