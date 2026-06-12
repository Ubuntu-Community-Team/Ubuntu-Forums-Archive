---
title: "KDE4 Install Error - Please Help -"
date: 2008-02-12
forum: Desktop Environments
---

### Post by ryanlhjess on 2008-02-12
I keep getting the following error when trying to install kde4

```
Selecting previously deselected package kde4-core.
Unpacking kde4-core (from .../kde4-core_3.3~gutsy1~ppa1_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-runtime-data_4%3a4.0.1-0ubuntu1~gutsy1~ppa1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by benerivo on 2008-02-12
You could try```
sudo apt-get install -f
```and if that fails to fix it, then you could also try```
sudo dpkg --configure -a
```

---

