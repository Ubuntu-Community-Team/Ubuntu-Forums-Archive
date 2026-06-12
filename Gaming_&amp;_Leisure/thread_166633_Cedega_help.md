---
title: "Cedega help"
date: 2006-04-26
forum: Gaming &amp; Leisure
---

### Post by ice.man on 2006-04-26
i keep getting this error and i just installed it

wine: '/home/moo/.cedega/Brothers in Arms/wineserver-ubuntu-root' must not be accessible by other users


wine: '/home/moo/.cedega/Steam/wineserver-ubuntu-root' must not be accessible by other users

can u help plz

---

### Post by frodon on 2006-04-27
Open a terminal and run a : ```
sudo chmod -R 777 /home/moo/.cedega
```The problem could just be too restrictive rights.

---

