---
title: "[SOLVED] Fluxbox - menu separator"
date: 2008-06-08
forum: Desktop Environments
---

### Post by Inxsible on 2008-06-08
How do you add a separator in the fluxbox menu?

I need a separator between my execs for Terminal, File Manager & the main fluxbox menu

---

### Post by p_quarles on 2008-06-09
Like so:
```
[exec] (File Manager) {/usr/bin/whatever}
[separator]
[submenu] (Everything Else)
```

---

### Post by Inxsible on 2008-06-09
> **p_quarles said:**
> Like so:
```
[exec] (File Manager) {/usr/bin/whatever}
[separator]
[submenu] (Everything Else)
```Thanks

---

