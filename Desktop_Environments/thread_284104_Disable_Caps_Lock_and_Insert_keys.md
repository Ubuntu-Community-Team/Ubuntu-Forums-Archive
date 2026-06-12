---
title: "Disable Caps Lock and Insert keys"
date: 2006-10-25
forum: Desktop Environments
---

### Post by kloper on 2006-10-25
What's the best solution for disabling the Caps Lock and Insert keys?

I know about the xmodmap command, but I don't want to type the command every time I have logged in.

xmodmap -e "clear Lock"
xmodmap -e "keycode 106 = "

I can also turn off the Caps Lock in xorg.conf in the keyboard section:

Option          "XkbOptions"    "ctrl:nocaps"

But I haven't figured out if I can do the same thing with the Insert key.

Cheers

Ubuntu Edgy 6.10 RC
Xorg 7.1.1
Gnome 2.16.1

---

### Post by Black_Monkey on 2006-12-21
I've been looking around trying to work out how to do this... has anyone got any idea?

---

### Post by doc symbiosis on 2007-01-21
I did it this way:

1) create an appropriate xmodmap-file:
```

xmodmap -pke > ~/.xmodmap.myown

```
2) Search the line with capslock in it, it's keycode 66 in my case. Replace it with something you wouls like, my line looks like this:
```

keycode  66 = slash backslash

```
so I have slash and backslash on my capslock.

3) make two entries for the xmodmap in autostart:
```

xmodmap -e "clear Lock"
xmodmap ~/.xmodmap.myown

```
with the first command, the capslock function is disabled, with the second the modified keymap is loaded.


I hope this helps.

---

