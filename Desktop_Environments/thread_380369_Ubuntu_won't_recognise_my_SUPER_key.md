---
title: "Ubuntu won't recognise my SUPER key"
date: 2007-03-09
forum: Desktop Environments
---

### Post by mwob on 2007-03-09
Hi all,

I have a standard (UK) keyboard. Ubuntu won't recognise my super key being pressed! By the super key I mean the "windows" key in between control and alt on the bottom left. Do I need to do anything to enable it?

My XOrg.Conf contains this:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Thanks!

---

### Post by dannyboy79 on 2007-03-09
well what do you want it to do? i would think you'd have to map it to something for it to do anything as isn't this key specific to windows functions?

---

### Post by mwob on 2007-03-09
I'm using Beryl, and in beryl, you can assign kb shortcuts for certain things. All of the shortcuts mapped using super key dont work, and if I try to use the "grab key" feature, it never picks up the super key!

---

### Post by Draku on 2007-03-09
Go to System &#8594; Preferences &#8594; Keyboard  and on the Layout Options at Alt/Win key behavior select Super is mapped to the Win-keys (default) 8)

---

### Post by mwob on 2007-03-10
Thanks Drako :) That sorted it!

---

