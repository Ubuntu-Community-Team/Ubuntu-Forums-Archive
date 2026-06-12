---
title: "two cursors in gnome"
date: 2005-01-18
forum: Desktop Environments
---

### Post by dninja on 2005-01-18
When I start gnome I get the standard X, x shaped, cursor in the middle of the screen but I also get the gnome arrow cursor. The X one is fixed, the other one works as normal.

Can anyone suggest why I get the second one?

---

### Post by tomchuk on 2005-01-19
Try adding:
```
        Option          "SWcursor"      "true"
```
to the device section of your /etc/X11/XF86Config-4

---

### Post by dninja on 2005-01-19
I'll try that tonight.

Something I noticed last night was that the second cursor disapears when a screensaver kicks in.

---

