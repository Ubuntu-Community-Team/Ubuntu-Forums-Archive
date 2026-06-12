---
title: "[SOLVED] Logout without prompt window?"
date: 2013-11-25
forum: Desktop Environments
---

### Post by martro on 2013-11-25
Hi, is there a way to programmaticaly logout from Lubuntu with lxsession-logout without this prompt window? Thanks

[CENTER][ATTACH=CONFIG]248084[/ATTACH]
[/CENTER]

---

### Post by martro on 2013-11-25
This works:

```
pkill -SIGTERM lxsession
```

---

