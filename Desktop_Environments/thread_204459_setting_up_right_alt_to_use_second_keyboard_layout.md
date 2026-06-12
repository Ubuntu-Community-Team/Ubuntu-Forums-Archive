---
title: "setting up right alt to use second keyboard layout using gnome"
date: 2006-06-27
forum: Desktop Environments
---

### Post by sup on 2006-06-27
I am Czech so I need to be able to write czech special signs, so I use czechia keyboard layout. However, labels on special sign keys of third and fourth level (that you normally acces throu right alt with or without shift) like /?'";:[{]}|\ and so on on my keyboard are according to US layout. Now I would like to be able to use czechia keyboard layout and after pressing right alt with or without shift, US layout. I know ho to do this with editing xorg ```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        #Option         "XkbLayout"     "cz"
        Option          "XkbLayout"     "cz,us"
        Option "XkbVariant" "qwerty," # my favorite variant of czechia layout
        Option "XkbOptions" "grp:switch,grp:shift_toggle"
```
however, I am failing to make this work through Gnome (which I would prefer, because there are also things I know how to configure with gnome only). Any ideas?

---

### Post by sup on 2006-06-29
hm, so editing /etc/X11/xkb/symbols/cz so that it follows symbols on my keys solved the problem, but it is not very user friendly - for I think most people in my country uses similar keyboard to mine

---

