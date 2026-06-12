---
title: "NetHack does not work with X11 frontend"
date: 2009-12-11
forum: Gaming &amp; Leisure
---

### Post by Tibuda on 2009-12-11
I have installed the nethack-x11 package to try a nicer way to play NetHack. It works fine in CLI, but when I try to use the X11 interface, it segfaults.

This is the terminal output of playing it in CLI and in X11:
```
$ nethack
Be seeing you...
$ NETHACKOPTIONS='windowtype:x11' nethack

Oops...
Program initialization has failed.
Report error to "root".
split: eos!
Segmentation fault
```

---

### Post by jamesstansell on 2009-12-27
Does the xnethack command work for you?

---

