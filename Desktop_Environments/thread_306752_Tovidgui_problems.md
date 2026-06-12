---
title: "Tovidgui problems"
date: 2006-11-25
forum: Desktop Environments
---

### Post by gu014 on 2006-11-25
hello,
after installing tovid and trying to run 'tovidgui' from the command line i encounter the following error message:
```
Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 39, in ?
    from libtovid.gui.frames import TovidFrame
  File "/usr/local/lib/python2.4/site-packages/libtovid/gui/frames.py", line 8, in ?
    from libtovid.tdl import Project
  File "/usr/local/lib/python2.4/site-packages/libtovid/tdl.py", line 11, in ?
    from libtovid.menu import Menu
  File "/usr/local/lib/python2.4/site-packages/libtovid/menu.py", line 17, in ?
    from libtovid.flipbook import Flipbook
  File "/usr/local/lib/python2.4/site-packages/libtovid/flipbook.py", line 66, in ?
    from libtovid.render.drawing import Drawing
  File "/usr/local/lib/python2.4/site-packages/libtovid/render/drawing.py", line 87, in ?
    import Image      # for JPG export
ImportError: No module named Image
```

all i did was a ./configure  and then sudo make install  before attempting to run 'tovidgui'

Any help would be appreciated.

---

### Post by taurus on 2006-11-25
I assume you want to an .avi to DVD so you can play it on your stand alone DVD player!  You can also use DeVeDe and it's in the repos...

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by gu014 on 2006-11-25
thank you.  i will give this a try as i was not particularly fond of tovid.

---

