---
title: "Where did QWERTY go?"
date: 2007-04-21
forum: Desktop Environments
---

### Post by Infamous Flame on 2007-04-21
Hey,

I'm not sure if this is the right forum for this question but it's the nearest I could find. I recently tried to install Beryl and had X die on me, but managed to get it restored by messing around in the recovery console. Anyways, for some reason, my keyboard layout has now defaulted to US English, which means, for example, the "speech marks" key, and the @ symbol have switched places.

Does anyone know how to switch this back? I can't find QWERTY in the keyboard layouts part of preferences in gnome, and the only UK ones seem to be Dvorak/MAC/other.

Thanks.

---

### Post by jocko on 2007-04-21
The keyboard layout is normally set by xorg.
To change it do this:
```
sudo gedit /etc/X11/xorg.conf
```Scroll down until you see this section:
```
Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
   [COLOR=Red][COLOR=Black] Option        "XkbLayout"[/COLOR] "se"[/COLOR]
    Option        "XkbOptions" "lv3:ralt_switch"
EndSection

```I guess you will see that the country code is "us" and you want it to be "gb".

---

