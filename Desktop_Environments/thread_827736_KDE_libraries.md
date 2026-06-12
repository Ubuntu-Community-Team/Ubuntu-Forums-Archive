---
title: "KDE libraries"
date: 2008-06-13
forum: Desktop Environments
---

### Post by oboedad55 on 2008-06-13
I am running Ubuntu Gnome with no KDE apps. However, I want to run Kompozer which requires a number of KDE libraries, etc. If I decide to uninstall Kompozer will the extra files get removed as well, or will I have to hunt through and remove them manually?

Thanks,

---

### Post by kellemes on 2008-06-13
> **oboedad55 said:**
> I am running Ubuntu Gnome with no KDE apps. However, I want to run Kompozer which requires a number of KDE libraries, etc. If I decide to uninstall Kompozer will the extra files get removed as well, or will I have to hunt through and remove them manually?

Thanks,

In order to remove unneeded packages you can do the following from a terminal window..
```
sudo apt-get autoremove
```

Edit: By the way, never accept blindly..

---

### Post by oboedad55 on 2008-06-13
> **kellemes said:**
> In order to remove unneeded packages you can do the following from a terminal window..
```
sudo apt-get autoremove
```

Edit: By the way, never accept blindly..

Thanks for the response. Using this command in my situation what do I autoremove?

Thanks,

---

### Post by dje on 2008-06-13
> **oboedad55 said:**
> Thanks for the response. Using this command in my situation what do I autoremove?

Thanks,

You do not need to specify any package with that command it automatically takes care of any unneeded dependencies every time you run it ;)

---

### Post by oboedad55 on 2008-06-13
> **dje said:**
> You do not need to specify any package with that command it automatically takes care of any unneeded dependencies every time you run it ;)

Thanks, that's excellent info for future use.

Peace,

---

