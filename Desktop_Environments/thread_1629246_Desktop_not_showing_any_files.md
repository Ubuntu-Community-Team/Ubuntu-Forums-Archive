---
title: "Desktop not showing any files"
date: 2010-11-23
forum: Desktop Environments
---

### Post by bigred1 on 2010-11-23
My desktop does not show any files or folders. When I try to drag a file there from Nautilus the "drop" of drag-and-drop fails. 

Yet the ~/Desktop folder appears fine in Nautilus; there are some files and folders there; and I can move new ones there.

How can I fix this?

---

### Post by stinkeye on 2010-11-24
Have you checked this setting?
```
gconf-editor /apps/nautilus/preferences/show_desktop

```

---

### Post by bigred1 on 2010-11-24
Thank you. It is set to true.

The desktop is not accepting anything  -- e.g., if I right click it, I get no context menu.

---

### Post by bigred1 on 2010-11-24
--

---

### Post by bigred1 on 2010-11-24
Thank you. Your advice did the trick. Actually, it was already set to true. I set it to false, closed gconf-editor , with no change. But then I opened gconf-editor  and set it to false, then closed gconf-editor  -- and the problem was resolved.

---

### Post by divineAngel on 2010-11-24
I have the same problem after recent update and on top of that i get the Starting File manager spaming windows

---

### Post by bigred1 on 2010-11-25
It just happened again. I don't know what caused it. I then ran gconf-editor /apps/nautilus/preferences/show_desktop  -- the checkbox was checked. I unchecked it; then rechecked it. 

The problem was resolved -- the icons reappeared, etc.

But I have no idea why this keeps happening.

---

