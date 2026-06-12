---
title: "Smeg won't start after installing Cairo"
date: 2006-01-25
forum: Desktop Environments
---

### Post by trevorv on 2006-01-25
I've just installed Cairo, and now Smeg won't run. Running from a terminal, I get
```
Traceback (most recent call last):
  File "/usr/bin/smeg", line 31, in ?
    from DialogHandler import DialogHandler
  File "/usr/lib/smeg/DialogHandler.py", line 30, in ?
    import gtk, gtk.glade
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden

```

And I have absolutely no idea how to fix that, so any help is appreciated. At the moment I'm stuck manually editing .desktop files, which isn't very fun!

---

### Post by trevorv on 2006-01-25
I'm getting exactly the same issue with gnome-btdownload, and so I'd imagine it's only a matter of time before other apps hit the problem.

---

