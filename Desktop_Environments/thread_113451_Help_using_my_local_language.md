---
title: "Help using my local language"
date: 2006-01-06
forum: Desktop Environments
---

### Post by antubis on 2006-01-06
I`m from Bulgarian and I want to use my language. How can I do that?
I try to do smth by using this:

> 
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us,bg"
        Option          "XkbVariant"    ",bds"
        Option          "XkbOptions"    "grp:alt_shift_toggle,grp:lwin_switch,grp_led:scroll"
EndSection


I installed mscorettfonts but still I can`t write in bulgarian language. So ... ?

---

### Post by John.Michael.Kane on 2006-01-06
Reinstall ubuntu, and select your country ect before the install, and your keyboard layout should then be in your language.

---

### Post by antubis on 2006-01-06
I already did this but there is no result!

---

### Post by Bretls on 2006-02-09
I use the keyboard prefs in gnome to do this "system>preferences>keyboard". You can add bulgarian as layout, but I noticed that the layout was a little off from my keyboard. The `~ were not there and the () were in the wrong spot. I edited the keymap to fix it. 

My xorg file looks like this:

Section "InputDevice"

    Identifier     "Generic Keyboard"

    Driver         "kbd"

    Option         "CoreKeyboard"

    Option         "XkbRules" "xorg"

    Option         "XkbModel" "pc104"

    Option         "XkbLayout" "us"

EndSection

I've attached the bg layout which should be placed in "/etc/x11/xkb/symbols" if you have the same problem with those keys. There is also a screenshot of the layout. Btw, backup your old layout just in case.

---

### Post by west4sider on 2007-10-11
> **Bretls said:**
> I use the keyboard prefs in gnome to do this "system>preferences>keyboard". You can add bulgarian as layout.

Just switched to Ubuntu and I didn't know how to write in Bulgarian but that helped me ... Thanks!

---

