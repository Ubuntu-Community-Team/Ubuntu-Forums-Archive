---
title: "Unity themes doing nothing with the panel nor window borders and title"
date: 2015-04-17
forum: Desktop Environments
---

### Post by lyonya2 on 2015-04-17
After I someday launched Ubuntu and recognized that Radiance theme won't change the color of window title and the panel color, I ended up deleting all themes from /usr/share/themes and then reinstalling light-themes again. The theme looks fine except for the window borders and the panel.

uname -a:
Linux ionagamed-laptop 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


[http://imgur.com/66cwtI7](http://imgur.com/66cwtI7)

---

### Post by lyonya2 on 2015-04-17
I srsly don't know why, but i ran compiz --replace once and it fixed the problem

---

### Post by CantankRus on 2015-04-17
You can use **gtk-theme-config** for some color tweaks.
```
sudo apt-get install gtk-theme-config
```
Log out and back in after applying changes.

---

