---
title: "How to reset default theme"
date: 2012-03-04
forum: Desktop Environments
---

### Post by statichippo on 2012-03-04
I installed Ubuntu 11.10 the other day and so far am very happy.  I installed MyUbuntu today and began playing around.  I didn't like the way things looked so I reset to default.  Everything is back to normal now except the look of my window toolbars (minimize, maximize buttons).  How do I reset this to the way it looked when Ubuntu was installed?

---

### Post by Krytarik on 2012-03-04
> **statichippo said:**
>  Everything is back to normal now except the look of my window toolbars (minimize, maximize buttons).  How do I reset this to the way it looked when Ubuntu was installed?
```
gconftool-2 --unset /apps/metacity/general/theme
```And just to be sure:
```
gconftool-2 --unset /apps/metacity/general/button_layout
```Regards.

---

