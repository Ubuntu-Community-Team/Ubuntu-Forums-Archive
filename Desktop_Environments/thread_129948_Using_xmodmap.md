---
title: "Using xmodmap"
date: 2006-02-15
forum: Desktop Environments
---

### Post by catfox on 2006-02-15
Hi All,
I'm trying to get my keyboard to let me produce some symbols that it won't do by defatult (at least, not easily)
For example, I've mapped a key to produce # with:
```

keycode 116 = numbersign

```
but I want to be able to do something similar when the alt key is pressed.
So something like

keycode 000 + keycode 111 = symbol 

but I can't figure out how to have two keycodes = something. trying it just assigns the symbol to each of the keycodes individually.

does anyone have any ideas?
cheers

---

### Post by frodon on 2006-02-15
You don't need 2 keycodes because you want to put the function on the same button.
I give you an exemple on how i remaped a key to "7" for small letters and "&" for capital letters : ```
xmodmap -e "keycode 16 = 7 ampersand"
```So if you want to add several characters on the same button just add them with a space between each in the xmodmap line.

EDIT: maybe i misunderstood what you want to do, if it's the case ... all my apologies

---

### Post by catfox on 2006-02-15
not sure if that'll work for me.
I know how to map single buttons, but what if I want to press alt + 3 so i get #

---

