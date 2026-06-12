---
title: "Trash icon not showing"
date: 2008-05-25
forum: Desktop Environments
---

### Post by gammyhand on 2008-05-25
Hi,

I have done the usual gconf-editor thing to show a trash icon on my desktop but it is not appearing (I have tried restarting x).

Any ideas?

---

### Post by konungursvia on 2008-05-25
Try putting one on your panel, if there is none there, by right clicking. Then try dragging that to where you want it.

---

### Post by gammyhand on 2008-05-25
I have one on my top panel but it won't let me drag it off there.

---

### Post by SkonesMickLoud on 2008-05-25
> **gammyhand said:**
> I have one on my top panel but it won't let me drag it off there.

Right click and untick "Lock To Panel".

Or enter:

```
gconftool-2 --type boolean --set /apps/nautilus/desktop/trash_icon_visible true
```

into a terminal.  Sure, it's basically the same as going through gconf-editor, but it may just work.

---

