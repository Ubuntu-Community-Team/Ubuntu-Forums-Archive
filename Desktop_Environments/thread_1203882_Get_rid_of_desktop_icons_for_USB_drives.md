---
title: "Get rid of desktop icons for USB drives?"
date: 2009-07-03
forum: Desktop Environments
---

### Post by Ulfgeir on 2009-07-03
This may be an easy fix, but I've looked everywhere in Gnome and can't find an option for it.  Basically, I want my USB pen drives to stop showing up as icons on my desktop.  They already appear under the "Places" menu, and that's more than sufficient for me.  I keep them plugged in on a nearly constant basis for backing up files, and I hate seeing them displayed on the desktop like that because I prefer to keep it as spartan as possible.

---

### Post by x33a on 2009-07-03
alt+f2 -> type gconf-editor,

apps -> nautilus -> desktop.

uncheck, volumes visible.

note: with this other drives too, will not be visible on the desktop.

---

### Post by Ulfgeir on 2009-07-04
That did the trick.  Thanks!

---

