---
title: "Can't Use Alt-Gr"
date: 2005-04-03
forum: Desktop Environments
---

### Post by bigblop on 2005-04-03
I am trying to set up the keyboard to Danish. I use FVWM as my Window Manager.

I can't type any charater that depends on Alt-Gr (AT, Backspace, Pipe, tilde etc.).
I have tried to do the following in my XF86Config-4 file:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
	Option		"XkbVariant"	"dk"
EndSection

I have tried to start KDE instead and there it works fine! But it never works when I get to the login screen.

Hope someone can help!

---

