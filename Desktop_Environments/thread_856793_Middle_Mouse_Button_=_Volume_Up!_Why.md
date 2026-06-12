---
title: "Middle Mouse Button = Volume Up! Why?"
date: 2008-07-11
forum: Desktop Environments
---

### Post by alterhut on 2008-07-11
Hi Ubuntuforums.org community!

Here's my issue: I'm using Ubuntu 8.04. When pressing the extra button of my Logitech MX1000 Mouse (tilting the scrollwheel to the left), gnome acts as if I'm pressing the key **0xb0** (which is usually mapped to "increase volume"). The same goes vice versa with decrease volume.

I'm a newbie and I got no clue what I could possibly do to solve it. Maybe it has to do something with my xorg.conf? Here are the relevant lines:

[PHP]Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"altgr-intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection[/PHP]

---

### Post by kerry_s on 2008-07-11
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "ButtonMapping" "1 2 3"
EndSection  
```

---

### Post by alterhut on 2008-07-11
An Update: It's actually not the middle mouse button, but the extra buttons of the Logitech MX1000. You can push the scroll wheel to the left or to the right and that triggers two other buttons. Which are somehow linked to volume up and volume down respectively. The middle mouse button has nothing to do with it.

So, is there a way to change that?
Just to stop those two extra buttons from doing anything.

---

### Post by kerry_s on 2008-07-11
[http://adventuresinswitching.blogspot.com/2007/12/getting-my-logitech-mx1000-mouse-to.html](http://adventuresinswitching.blogspot.com/2007/12/getting-my-logitech-mx1000-mouse-to.html)

---

