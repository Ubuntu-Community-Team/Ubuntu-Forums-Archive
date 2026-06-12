---
title: "Keyboard does not work correctly =&gt; XGL bug?"
date: 2007-01-29
forum: Desktop Environments
---

### Post by Seb1982 on 2007-01-29
Hi everyone!

I made XGL and Beryl work a few days ago but now I'm confronted with a different problem: My KEYBOARD does not work correctly!!!

I'm using Ubuntu 6.10 and a regular 105-key device with US layout. Due to the fact that I have to type a lot of special characters I'm using it in "us_intl" mode.

E.g. for typing the "ß" I usually have to hold down the right ALT key and press "S". But now no combination with the right ALT key works!

My xorg.conf file:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

Does anyone have an answer?

Thanks a lot!

Sebastian

---

### Post by tanguyr on 2007-01-30
> **Seb1982 said:**
> Hi everyone!
E.g. for typing the "ß" I usually have to hold down the right ALT key and press "S". But now no combination with the right ALT key works!


Hi Sebastien,

Check out [this thread]("http://www.ubuntuforums.org/showthread.php?t=291518").

Regs,
/t

---

### Post by Seb1982 on 2007-02-05
Thanks a lot!

Adding the line

```
xmodmap /usr/share/xmodmap/xmodmap.us-intl
```

to my starting programmes solved the problem!

Seb

---

