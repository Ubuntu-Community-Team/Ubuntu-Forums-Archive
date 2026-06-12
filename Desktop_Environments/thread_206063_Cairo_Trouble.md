---
title: "Cairo Trouble"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Permafrost91 on 2006-06-29
I am trying to run alacarte when I get this message:
```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in ?
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.4/site-packages/Alacarte/MainWindow.py", line 19, in ?
    import gtk, gtk.glade, gmenu, gobject
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 45, in ?    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: png_set_gray_1_2_4_to_8

```

I'm running 64bit Dapper and alacarte has worked for me before. I'm not sure what the problem is. I tried recompiling stable cairo packages without success. Any ideas on how to fix this?

---

### Post by Permafrost91 on 2006-06-29
I figured it out ... 

/usr/lib/libcairo.so.2 was pointint to /usr/lib/libcairo.so.2.8.0 but should be pointing to libcairo.so.2.2.4 (probably my "upgrade" was incompatible).

At any rate, it's fixed! If anyone knows what caused the problem, however, please let me know. I'd be curious.

---

