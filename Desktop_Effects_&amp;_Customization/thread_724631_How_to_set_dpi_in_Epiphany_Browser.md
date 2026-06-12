---
title: "How to set dpi in Epiphany Browser"
date: 2008-03-14
forum: Desktop Effects &amp; Customization
---

### Post by lvlo on 2008-03-14
Just open Epiphany preferences file:

```
sudo gedit /etc/gnome/epiphany/default-prefs.js
```

and add line:

```
pref("layout.css.dpi", 96);
```

You can set your own value of dpi.

That's all :)

---

