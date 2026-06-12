---
title: "can't move detached toolbar"
date: 2005-11-03
forum: Desktop Environments
---

### Post by jnoreiko on 2005-11-03
I detached the toolbar from Gedit and now I can't put it back.
I can see the little verticle bar on the left that I'm supposed to grab it with, but it doesn't respond to a mouse click.

Closing & relaunching it fixed the problem, but it's not just Gedit -- I've tried a few other apps and they have it too.

Which component should I file a bug under?

---

### Post by wylfing on 2005-11-03
Definitely buggy. You can move it around with the "move window" action (which is by default Alt+mouse) but you can't get it to reattach. More observed behaviors:

1. When you detach the toolbar, as long as you don't let go of it you can still reattach it.

2. You can Alt+right click and choose to close the toolbar. It will happily oblige. However, in the main application, the toolbar will still be set as "visible" and any attempt to change the toolbar's state will very likely crash the application.

---

