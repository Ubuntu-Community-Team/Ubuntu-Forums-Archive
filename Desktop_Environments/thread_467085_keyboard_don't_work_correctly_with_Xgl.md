---
title: "keyboard don't work correctly with Xgl"
date: 2007-06-07
forum: Desktop Environments
---

### Post by cadoro on 2007-06-07
When i run the Xgl on display :1 because i have an ati some key as  min X,windows key dont'work.
In Sistem->Preference->Keyboard i have set generic keyboard 105 and layout ita
This is my Xorg.conf
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "it"
EndSection

In session-gnome i have set to run 
setxkbmap -model pc105 -layout it 
but nothing

---

### Post by sambehera on 2007-07-21
> **cadoro said:**
> When i run the Xgl on display :1 because i have an ati some key as  min X,windows key dont'work.
In Sistem->Preference->Keyboard i have set generic keyboard 105 and layout ita
This is my Xorg.conf
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "it"
EndSection

In session-gnome i have set to run 
setxkbmap -model pc105 -layout it 
but nothing

im having the same problem... xgl seems to have some problem with keyboard configuration... my left super (windows) key and right alt key dont work in xgl.. havent found a solution for this yet... any help would be appreciated...

---

