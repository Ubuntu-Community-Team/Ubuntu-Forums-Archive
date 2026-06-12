---
title: "Can no longer connect to blizzard's battle.net after upgrading to kubuntu 7.10"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by exhume on 2007-10-19
Ever since I upgraded to kubuntu 7.10, I can no longer connect to to blizzard entertainment's battle.net via warcraft 3. Anyone else having this problem or have any idea's on fixing it?

---

### Post by Colro on 2007-10-19
The latest WINE is bugged for Warcraft 3 and won't let it use battle.net. I got around this by uninstalling WINE

```
sudo apt-get remove wine
```

and then re-installing an older version:

[http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.43~winehq0~ubuntu~7.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.43~winehq0~ubuntu~7.04-1_i386.deb)

0.9.43 works fine for me. Vote for the bug here if you'd like:
[http://bugs.winehq.org/show_bug.cgi?id=9787](http://bugs.winehq.org/show_bug.cgi?id=9787)

---

### Post by exhume on 2007-10-19
thanks a bunch man

---

### Post by hotweiss on 2007-11-25
I voted... It should be easy to fix as it was working before.

---

