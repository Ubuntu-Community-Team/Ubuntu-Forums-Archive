---
title: "Compiz setting changing itself magically"
date: 2010-12-17
forum: Desktop Environments
---

### Post by dennis90 on 2010-12-17
Hi!

When I try to set the Window Decoration match from the one that the panel applet Window Buttons configured for me (to hide decoration for maximized windows), it changes back magically.
Also, I can't disable the plugin. After unticking it, it puts the tick back in 1 or 2 seconds and nothing happens, not even a decorator restart.

I already cleared my whole gconf settings and Window Buttons should not be running now.

What should I do?

---

### Post by Krytarik on 2010-12-18
I would uninstall the Window Buttons applet altogether. You don't have to use this applet to manipulate when the window decoration takes place, as you apparently figured out.

This entry works on maximized windows:
```
!(state=maxvert & state=maxhorz)
```
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

---

### Post by dennis90 on 2010-12-18
Thank you.
I will try to do so as soon as I'll have a little time.

---

