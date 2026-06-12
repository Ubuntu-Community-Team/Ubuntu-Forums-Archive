---
title: "Menu editor not working"
date: 2006-01-17
forum: Desktop Environments
---

### Post by casfindad on 2006-01-17
I am running ubuntu and kubuntu on my desktop. My kde menu editor works fine, but smeg does not seem to work when I'm running gnome. If I right-click "Applications" and choose "Edit Menu", the cursor spins but then the process quits. If I start smeg in the terminal, I get the following output:

```
Traceback (most recent call last):
  File "/usr/bin/smeg", line 31, in ?
    from DialogHandler import DialogHandler
  File "/usr/lib/smeg/DialogHandler.py", line 30, in ?
    import gtk, gtk.glade
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden
```

Any suggestions for fixing this would be sincerely appreciated.

casfindad

---

