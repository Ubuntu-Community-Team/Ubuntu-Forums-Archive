---
title: "How to disable Alt+F8 shortcut in Gnome?"
date: 2011-02-03
forum: Desktop Environments
---

### Post by Zeemvel on 2011-02-03
How do I disable the Alt+F8 shortcut combination in Gnome? This shortcut does "resize window". However I don't want Gnome to override that shortcut, I want to be able to use it in IntelliJ.

Anyway, the obvious way to disable it, that is, remove it in the "Keyboard Shortcuts" option, does not disable it. Alt+F8 still does the resize window thing.

How do I REALLY disable it?

Thanks!

---

### Post by Zeemvel on 2011-02-04
Does nobody know this?

Thanks.

---

### Post by Frogs Hair on 2011-02-04
This is from the keyboard shortcut key help button .

---

### Post by Forlong on 2011-02-04
> **Zeemvel said:**
> How do I disable the Alt+F8 shortcut combination in Gnome? This shortcut does "resize window". However I don't want Gnome to override that shortcut, I want to be able to use it in IntelliJ.

Anyway, the obvious way to disable it, that is, remove it in the "Keyboard Shortcuts" option, does not disable it. Alt+F8 still does the resize window thing.

How do I REALLY disable it?
This particular setting is for the window manager in use. So you need to reload that.
Try running this command via [Alt]+[F2]
```
metacity --replace
```

---

