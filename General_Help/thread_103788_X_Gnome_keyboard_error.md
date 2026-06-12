---
title: "X /Gnome keyboard error"
date: 2005-12-14
forum: General Help
---

### Post by nb- on 2005-12-14
When I log into gnome, i get an error windows saying that my X keyboard conf is different from my gnome one.  This isnt a real problem but still.

gnome settings are;

Generic 105-key (Intl) PC
keybaord layout gb

and X settings are;

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbVariant"    "basic"
EndSection

Also when I change the gnome keyboard from Generic 105-key (Intl) PC to MS office keyboard, which is what i have, but when I do this the "end" key stops working.

---

### Post by andyakadum on 2007-10-14
I have exactly the same problem.  Its really annoying.

My settings are exactly the same as yours.  They appear to be the same but give me this stupid error.

There are other reports of this online as well.

Edit: BTW, are you also using the Gutsy beta?

---

