---
title: "pypanel error"
date: 2006-06-15
forum: Desktop Environments
---

### Post by graabein on 2006-06-15
I've seen this other places but I think it's all in breezy forums so here we go again: Is pypanel busted in universe? I get this error:

```
Traceback (most recent call last):
  File "/usr/bin/pypanel", line 957, in ?
    PyPanel(display.Display())
  File "/usr/lib/python2.4/site-packages/Xlib/display.py", line 80, in __init__
    self.display = _BaseDisplay(display)
  File "/usr/lib/python2.4/site-packages/Xlib/display.py", line 67, in __init__
    apply(protocol.display.Display.__init__, (self, ) + args, keys)
  File "/usr/lib/python2.4/site-packages/Xlib/protocol/display.py", line 123, in __init__
    self.default_screen = min(self.default_screen, len(self.info.roots) - 1)
  File "/usr/lib/python2.4/site-packages/Xlib/protocol/rq.py", line 1371, in __getattr__
    raise AttributeError(attr)
AttributeError: roots
```

---

### Post by zikki on 2006-06-16
Look here: 
[http://www.linuxforums.org/forum/linux-desktop-x-windows/50612-pypanel.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/50612-pypanel.html)

---

