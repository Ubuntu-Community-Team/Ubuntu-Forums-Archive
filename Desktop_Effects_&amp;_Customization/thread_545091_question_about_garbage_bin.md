---
title: "question about garbage bin"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by sp0onman on 2007-09-07
hello tis my first post.

just wanna know how i can move the garbage bin to the desktop? instead of being locked onto the  panel.

---

### Post by distroman on 2007-09-07
Hi

Put the following in a terminal.
```
gconf-editor &
```
Navigate to "/apps/nautilus/desktop/trash_icon_visible" enable it.

---

