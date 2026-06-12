---
title: "how to reinstall unity?"
date: 2012-01-15
forum: Desktop Environments
---

### Post by hans01 on 2012-01-15
I tested out Unity 5, and of course, it broke things, so I tried downgrading by

sudo apt-get install ppa-purge
sudo ppa-purge ppa:unity-team/staging
It removed Unity completely.

apt-get install unity
but the login screen now offers only Gnome.

How do I get back to Unity 4?

Thanks!

---

### Post by Krytarik on 2012-01-15
Try this:
```
sudo apt-get install --reinstall ubuntu-desktop
```Hope it works.

---

