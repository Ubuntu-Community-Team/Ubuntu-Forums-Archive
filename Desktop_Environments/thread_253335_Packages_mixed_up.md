---
title: "Packages mixed up"
date: 2006-09-08
forum: Desktop Environments
---

### Post by machuidel on 2006-09-08
After re-installing "libvte" and some other packages I received the following error when starting the "gnome-terminal":
undefined symbol: vte_terminal_set_opacity

It seems that my currently installed version of "libvte" does not support transparency anymore.

Now after removing and re-installing the "gnome-terminal" another version got installed (downgraded). One that does work but without transparency support :(.

Another version of "libfreetype6" got installed as well which has poorer font rendering (or with some hinting algorithm disabled).

Where can I still find the ones with transparency support?

I attached my sources.list.

---

### Post by machuidel on 2006-09-08
Okay. It works again. I found the old packages in "/var/cache/apt/archive" and installed them by hand. It seems they were removed from the repository.

---

