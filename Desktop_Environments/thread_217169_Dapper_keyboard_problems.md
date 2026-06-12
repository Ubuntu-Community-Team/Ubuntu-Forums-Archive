---
title: "Dapper keyboard problems"
date: 2006-07-16
forum: Desktop Environments
---

### Post by bmgz on 2006-07-16
I have a "microsoft natural pro" keyboard with British layout. When I upgraded to dapper, things went pear shaped. Most of my keys would output strange broken characters. I went to the Keyboard settings in gnome and pressed reset to default and things seemed fine after that.

Now I installed XGL and none of the shortcuts worked. I went to the keyboard setting and selected "microsoft natural pro" witn United Kingdom layout. Now XGL shortcuts work again, but my keyboard isn't working again. I can't seem to use the double and single qoutation marks in particular some other characters are also broken.
I do an xmodmap for the UK layout and that fixes the keyboad. But then XGL does'nt work again? everything was fine in Breezy, something broke along the way, any ideas how I can remedy this annoyance?

---

### Post by bluecherry on 2006-07-16
I've had similar problems and the solution was to edit my xorg.conf file.

Apparently Gnome and Xorg both have a way of configuring your keyboard layout so I guess this works the same for XGL?

---

### Post by bmgz on 2006-07-17
> **bluecherry said:**
> I've had similar problems and the solution was to edit my xorg.conf file.

What exactly did you do?

---

### Post by bluecherry on 2006-07-17
I changed the keyboard entry to match te settings I use in gnome and since then everythin works fine... 

Don't know if your problems will be solved? (fingers-crossed ;))

```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "be"
EndSection

```

---

### Post by bmgz on 2006-07-17
It seems to be something to do with the british layout, when i select usa from the gnome-keyboard-swithcher-applet-thingy everything is dandy (except the key mappings ofcourse), but when I select GBr it gives me borked characters like this: ¨ and ´ (that is double and single quotation respectively)

---

