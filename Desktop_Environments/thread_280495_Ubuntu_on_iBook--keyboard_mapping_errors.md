---
title: "Ubuntu on iBook--keyboard mapping errors"
date: 2006-10-19
forum: Desktop Environments
---

### Post by carla on 2006-10-19
I've tried setting the keyboard mapping, with no success. The only way to type a capital letter is with the caps lock key; the shift key does nothing at all. I also cannot access the characters above the number keys, even with the caps lock key.

Any suggestions?

setup--
ibook dual-usb g3
gnome, ubuntu breezy, metacity

No other oddities or conflicts seem to exist. ](*,)

---

### Post by raul_ on 2006-10-19
did u try System -> Preferences -> Keyboard and play with the settings there?

---

### Post by carla on 2006-10-19
I've tweaked that, but with no success. Maybe my exact settings there might help suss out the problem:

layout--keyboard model = macintosh
layout options--alt/win = default; capslock key behavior = default.

it's as if the computer recognized my shift key, and now it doesn't. :confused:

---

### Post by raul_ on 2006-10-19
See if this helps
> 5.4 Keyboard Mapping

I saw lots of different information about this,
all the keymap shipped with your XFree will be in /usr/X11R6/lib/X11/xkb/symbols/macintosh/
I copied the folliwng keymap to /usr/X11R6/lib/X11/xkb/symbols/macintosh/fr_new:
New French keymap

fr_new **(this is a link)**
How to find the keys I need to change ?

Example:

You will probably need the pipe, also known as bar:
Open fr_new, and look for 'bar', you will get there

        key <AC09> {     [         l,    L               ],
                    [   notsign,    bar             ]       };

It means that a certain key is used for l (small L) when not using modifiers, L when combined with Shift, notsign with Alt and | with Alt and Shift.

InputDevice Section in XF86Config-4

    Section "InputDevice"
           Identifier      "..."
           Driver          "Keyboard"
           Option "Protocol"       "Standard"
           Option "AutoRepeat"     "250 30"
           Option "LeftAlt"        "Meta"
           Option "RightAlt"       "Meta"
           Option "ScrollLock"     "Compose"
           Option "RightCtl"       "Control"

           Option "XkbLayout"     "macintosh/fr_new"
    EndSection

---

