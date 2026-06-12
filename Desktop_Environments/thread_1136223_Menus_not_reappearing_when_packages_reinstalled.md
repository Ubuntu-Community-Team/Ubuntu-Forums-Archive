---
title: "Menus not reappearing when packages reinstalled"
date: 2009-04-24
forum: Desktop Environments
---

### Post by snuwoods on 2009-04-24
I've realized the problem when I reinstalled wine.  I had first uninstalled it, and deleted the menu.  Now however, when it is installed again - the menu does not appear under applications.
Is this a known problem?  Am I doing something wrong?

---

### Post by postOSX on 2009-04-25
I'm having the exact same problem. Bump!

In the mean time, how do I run Windows Firefox from the terminal?

---

### Post by snuwoods on 2009-04-25
I figured how to get the menus to "reappear".
It still isn't fixed by any means, but if you find the file:
/etc/xdg/menus/applications-merged/wine.menu
using sudo - delete it.
your menu should reappear, but under the "other" menu.

---

