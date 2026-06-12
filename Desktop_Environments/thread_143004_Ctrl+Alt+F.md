---
title: "Ctrl+Alt+F*"
date: 2006-03-11
forum: Desktop Environments
---

### Post by christhemonkey on 2006-03-11
When on my new(er) computer, typing Ctrl alt and F1 through 4 no longer takes me to tty, it just sits there and does nothing!
Any ideas?

---

### Post by Aine on 2006-03-11
whats in your xorg.conf for your keyboard

---

### Post by christhemonkey on 2006-03-11
will post it ASAP, but im going to bed now.

---

### Post by christhemonkey on 2006-03-12
My xorg.conf's section about keyboard:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

```

---

### Post by Lord Illidan on 2006-03-12
Try and replace it with this: 
```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection
```

---

### Post by christhemonkey on 2006-03-13
This didn't work!
Oh eck!
Any more ideas?
Oh found out that in a gnome-terminal Doing Ctrl+Alt+F1 through 4 gives P,Q,R,S respectively and then 5 throuhg 8 give me :f or something.

---

