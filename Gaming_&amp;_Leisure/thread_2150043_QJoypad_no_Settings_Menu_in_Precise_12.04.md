---
title: "QJoypad no Settings Menu in Precise 12.04?"
date: 2013-05-30
forum: Gaming &amp; Leisure
---

### Post by OrangeVixen on 2013-05-30
Has anyone else installed QJoypad (from the games repository) on Precise?

If so, is it just me or is the "Configure" item missing from the menu? I ran it and it displayed on the panel but there is no menu item to configure anything, so I am stick with just the default "No Layout" item.

---

### Post by Solid One on 2013-05-31
It seems to be an issue related to Unity and its indicators.

A workaround is running it without tray, just like this:

```
qjoypad --notray
```

---

### Post by OrangeVixen on 2013-05-31
Ah, now I see, it seems that clicking the left mouse button on the icon maps the configuration dialog.

If you run it on the panel (without the --notray) the panel (on Precise 12.04) seems to send the signal to map the menu (as if the right mouse button was pressed) instead of the left mouse button to map the configuration dialog.

Maybe someone can hack the code in qjoypad to add the Map Configuration Dialog item to the menu.

---

