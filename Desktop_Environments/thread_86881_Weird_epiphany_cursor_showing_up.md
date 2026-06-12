---
title: "Weird epiphany cursor showing up"
date: 2005-11-06
forum: Desktop Environments
---

### Post by bigdufstuff on 2005-11-06
I don't know what I did but some how a blinking text cursor always shows up in epiphany now. This inside a normal paragraph tag. It very distracting and makes it hard to scroll. Instead of up and down scrolling it now moves the cursor. It didn't do this before and firefox still doesn't do this. I would prefer to use epiphany but without this "feature" any idea how to go back to how it was.

---

### Post by Ampersand on 2005-11-06
If this is just an epiphany problem, it might be solved by renaming the .gnome2/epiphany folder (in your home directory).

---

### Post by bigdufstuff on 2005-11-06
You would think that would work. That removed all my settings, but the cursor still showed up. I just double checked and the cursor does not show up in firefox, only in epiphany.

---

### Post by ow50 on 2005-11-06
Some of Epiphany's settings are stored in gconf, so removing the profile ~/.gnome2/epiphany is not enough.

Try running the following command
```
gconftool-2 --type bool --set /apps/epiphany/web/browse_with_caret 0
```
or use the gconf-editor to do the same.

---

### Post by bigdufstuff on 2005-11-06
aha! that fixed it. Thank you very much!!

---

