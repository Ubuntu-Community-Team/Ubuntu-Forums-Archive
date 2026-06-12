---
title: "kdelibs4c2a"
date: 2007-03-04
forum: Desktop Environments
---

### Post by DapperMe17 on 2007-03-04
Hi,

Kubuntu Edgy



Mistakingly, I uninstalled a portion of "kdelibs4c2a" :( 

I'm left without adept, as well as many other KDE items.



I tried reinstalling via apt-get, but most of the desktop & programs are missing.



Can I do a restore?



Thanks

---

### Post by Jucato on 2007-03-04
kdelibs is the base upon which all KDE-related apps are built. So most probably, a lot more than kdelibs itself was removed.

Try to reinstall the **kubuntu-desktop** package

```
sudo apt-get install kubuntu-desktop
```

This will reinstall all the packages that are installed in a default Kubuntu system.

Hope this helps.

---

### Post by DapperMe17 on 2007-03-04
Thank you very much!

---

