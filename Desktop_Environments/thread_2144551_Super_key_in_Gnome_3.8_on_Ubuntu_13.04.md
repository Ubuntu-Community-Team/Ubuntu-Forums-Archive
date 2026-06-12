---
title: "Super key in Gnome 3.8 on Ubuntu 13.04"
date: 2013-05-12
forum: Desktop Environments
---

### Post by rubjo on 2013-05-12
When I have no windows open, the super key does not open the Activities / Overview screen. With any window visible, it works.

Incidentally, Guake Terminal, which is set to open when F12 is pressed, shows the exact same behaviour.

Is this reproducible by someone else? Is it a known bug (or a feature ;-)) ?

---

### Post by markbl on 2013-05-12
I've never heard of that before. Disable all your extensions, restart gnome shell, and confirm whether it now works.

---

### Post by rubjo on 2013-05-13
Thanks for replying.

I've done a bit more testing now, and it's the same with all extensions disabled for me.

I have the "Have file manager handle the desktop" option turned off in Tweak Tool (to be able to have a desktop background image). With the option turned on instead, the bug disappears.

To reproduce the issue, I have to:
1. Log in
2. Open any window, e.g. a Terminal or Files window, then close it.

After this point, whenever no windows are open, the Super key doesn't open the Activities screen.

---

### Post by markbl on 2013-05-13
Hmm, strange one. Certainly does not happen for me on 13.04 64 bits + intel HD4000 although I have been reporting a somewhat similar bug (for a couple of years!) in GNOME Shell at [https://bugzilla.gnome.org/show_bug.cgi?id=660922](https://bugzilla.gnome.org/show_bug.cgi?id=660922).

---

