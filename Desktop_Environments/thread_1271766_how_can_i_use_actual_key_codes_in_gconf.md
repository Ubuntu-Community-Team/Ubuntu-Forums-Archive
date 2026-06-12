---
title: "how can i use actual key codes in gconf?"
date: 2009-09-21
forum: Desktop Environments
---

### Post by gwydionwaters on 2009-09-21
what i mean by actual is the numeric value. some on my keys, on a powerbook g4, have no names. so instead of alt_l and such i have 169 and 232 etc for a few multimedia keys. i tried just entering the code where one would assign <alt> or whatever but that didn't work. any ideas?

---

### Post by VCoolio on 2009-09-21
Open a terminal, enter "xev" (it will bring up a little window with a square in it), press the key you need and reed the output. Is there something like "XF86blahblah" in it, then you can use that.

---

### Post by gwydionwaters on 2009-09-21
these come up as no symbol. i made an attempt at using Xmodmap to assign keysym's but it doesn't seem to read my file. it does load the file at start up but my entries seem ineffective.
```

keycode 232 = brdown
keycode 233 = brup
keycode 169 = eject

```is this incorrect format?

**
i realized that the default gnome keyboard shortcut utility allows me to use eject if i change it from XF86Eject to 0xa9, still working on the others though. after the file is loaded xev still say's no symbol..

---

