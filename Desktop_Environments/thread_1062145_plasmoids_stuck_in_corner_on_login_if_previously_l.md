---
title: "plasmoids stuck in corner on login if previously locked"
date: 2009-02-06
forum: Desktop Environments
---

### Post by Mindless Automata on 2009-02-06
If I lock my widgets in place on my desktop, and then reboot the window manager and re-login, all my widgets such as the lcd-weather, rss, dictionary, and icons that were on my desktop are stuck in the upper-left corner.

It almost seems like, for some stupid reason, the widgets are placed on the desktop at the corner and are then moved to the correct location; if locked, the widgets cannot be moved and thus stay there.  This seems like very dodgy behavior to me, is there a workaround, is this a known bug, or what?

---

### Post by Mindless Automata on 2009-02-06
Actually, it's a bit more naunced like that.  Some of them don't get placed in the right location, and only a few particular ones stay in the corner if the widgets were locked.

There seems to be some sort of randomness here so I'm nto sure how to describe the behavior fully.

---

### Post by Mindless Automata on 2009-02-06
I fixed this by taking an extreme measure and deleting my .kde folder and rebuilding everything from scratch.  Not fun, but whatever, it works now.

---

