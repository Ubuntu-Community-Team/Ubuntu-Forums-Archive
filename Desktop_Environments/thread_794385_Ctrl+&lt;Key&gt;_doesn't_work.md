---
title: "Ctrl+&lt;Key&gt; doesn't work"
date: 2008-05-14
forum: Desktop Environments
---

### Post by Okuryo on 2008-05-14
Hello,
I use two keyboard layouts: [FONT="Courier New"]us[/FONT] (English) and [FONT="Courier New"]il[/FONT] (Hebrew).
I upgraded from Gutsy to Hardy about a week ago, and ever since, [FONT="Courier New"]Ctrl+<Key>[/FONT]s have strange behavior in some applications.

In Terminal, when I press [FONT="Courier New"]Ctrl+C[/FONT], it just writes '&#1489;' (which is the letter in Hebrew that shares a key with 'C'). Similarly, when I press [FONT="Courier New"]Ctrl+D[/FONT] I get '&#1490;'.

In OpenOffice 2.4, [FONT="Courier New"]Ctrl+<Key>[/FONT]s just don't work when I'm on the Hebrew layout. Same in Firefox 2 (but in the latter it's been this way before Hardy).

Is there a way to fix this situation? In Gutsy it was alright.

This is the keyboard section in my xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,il"
	Option     	"XkbOptions" 	"grp:switch,grp:alt_shift_toggle,grp_led:scroll"
EndSection
```

---

### Post by imon9 on 2008-05-14
could it be that the system uses "Ctrl" key as drag window hot-keys

please set another key for that purpose, eg: (super) key

---

### Post by Okuryo on 2008-05-14
Thanks, but I don't see how that make '&#1489;' show instead of 'C'.

Also, it appears that Alt is he drag-windows key, not Ctrl. Which file sets that?

---

### Post by Okuryo on 2008-05-15
Okay, the OpenOffice problem got fixed somehow (perhaps temporarily) when I closed it and opened it again.

The Ctrl-Key-Hebrew-switching problem in the Terminal still persists.

---

