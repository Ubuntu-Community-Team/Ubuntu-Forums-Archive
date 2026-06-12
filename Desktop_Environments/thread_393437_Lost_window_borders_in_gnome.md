---
title: "Lost window borders in gnome"
date: 2007-03-25
forum: Desktop Environments
---

### Post by bobcat26tx on 2007-03-25
My laptop crashed from lose of power (running Edgy).  At the next bootup gnome starts programs without borders, so they can't be closed or moved.

Something similar happened to me with KDE in RH and I simply cleaned some .kde files and temp and it was fixed.  

How do I get my borders back?

---

### Post by hikaricore on 2007-03-25
Open a terminal and try:

```
metacity --replace
```

If that doesn't work you may have to go into your Themes menu under preferences and select
a different theme.  Perhaps there was file corruption.

Also by any chance are you running beryl or compiz?

---

### Post by bobcat26tx on 2007-03-25
The metacity --replace worked.  

Thanks much..:)

---

### Post by true_friend on 2008-02-19
Thnx I had similiar problem after uninstallign default compiz...fixed by metacity --replace command.

---

