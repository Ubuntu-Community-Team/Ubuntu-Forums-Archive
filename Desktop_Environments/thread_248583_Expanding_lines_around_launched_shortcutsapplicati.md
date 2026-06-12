---
title: "Expanding lines around launched shortcuts/applications"
date: 2006-09-01
forum: Desktop Environments
---

### Post by lozenge on 2006-09-01
In gnome, in a default install of Ubuntu, is there a way to remove or turn off the line that expands from the point of click when a shortcut is run? It expands over the entire desktop and disappears then the app launches, but I was wondering if I could disable it in any way.

Thanks.

---

### Post by Ramses de Norre on 2006-09-01
```
gconf-editor /apps/panel/global
```
and uncheck "enable_animations".

---

