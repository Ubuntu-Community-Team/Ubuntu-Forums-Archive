---
title: "keyboard layout in E17"
date: 2008-03-18
forum: Desktop Environments
---

### Post by n-alexander on 2008-03-18
I added a Cyrillic layout in Gnome and it worked, but in Enlightenment I only have the US.

How do I add a keyboard layout in Enlightenment?

---

### Post by dimvision on 2008-05-06
elive panel -> user conf -> root terminal

cd /etc/X11
cream xorg.conf

edit file to look like that 
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,de"
	Option      "XkbOptions" "grp:alt_shift_toggle"
EndSection

it works for german - us keyboard
change this line for ur country layout

Option		"XkbLayout"	"us,de"

sorry for my bad english..

---

### Post by smartboyathome on 2008-05-07
That isn't available outside of elive, but you can type gksu gnome-terminal in the run box, and it will open a root terminal. Then you can do the rest how you stated.

---

### Post by n-alexander on 2008-05-11
> **dimvision said:**
> elive panel -> user conf -> root terminal

cd /etc/X11
cream xorg.conf

edit file to look like that 
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,de"
	Option      "XkbOptions" "grp:alt_shift_toggle"
EndSection

it works for german - us keyboard
change this line for ur country layout

Option		"XkbLayout"	"us,de"

sorry for my bad english..

thanks. Another question is how to tell it to be a winkey layout

---

