---
title: "switching keyboard layout with ctrl+shift - is it possible at all?"
date: 2005-12-28
forum: General Help
---

### Post by bepcyc on 2005-12-28
I know that kxkb can't do this trick, and KDE does not like using two meta-keys as hotkey
I also know that trick with xorg.conf (from my local file):

> Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,ru(winkeys)"
        Option          "XkbVariant"    "winkeys"
        Option          "XkbOptions"    "grp:ctrl_shift_toggle,grp_led:scroll"
EndSection

it doesn't work for me - and I don't know why ;(

I'm tired of switching layout with Ctrl+Alt+K - it's a stupid hotkey - I hate it

does anybody have the same problem?

---

### Post by ingo on 2005-12-28
go to terminal and type "sudo kcontrol"

select Regional & Accessability

select keyboard shortcuts

in the selected (first) tab scroll right down to the bottom and select Keyboard-Switch to Next Leyboard Layout

you can now adjust the shortcut as you see fit. I've got ALT+Shift+A

while you're at it, select the third tab entitled "Application Shortcuts" and play around :)

---

### Post by bepcyc on 2005-12-28
yeah, I know this thing

but what about using 2 keys like ctrl+shift?

---

### Post by ingo on 2005-12-28
no reason why it shouldn't work, havn't tried it though...

---

### Post by bepcyc on 2005-12-28
then just try it ;))

---

