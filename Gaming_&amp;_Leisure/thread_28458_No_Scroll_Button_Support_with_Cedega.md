---
title: "No Scroll Button Support with Cedega"
date: 2005-04-20
forum: Gaming &amp; Leisure
---

### Post by michealm on 2005-04-20
When playing windows native games like Medal of Honor Series or even Quake 3 Windows native I cannot use my scroll button to change weapons, andy idea how to fix this?

---

### Post by shakin on 2005-04-20
[QUOTE=michealm]When playing windows native games like Medal of Honor Series or even Quake 3 Windows native I cannot use my scroll button to change weapons, andy idea how to fix this?[/QUOTE]

Your mouse is probably an MS Intellimouse Explorer (or another one using that driver). You need to add z axis mapping for those buttons in xorg.conf.

In your mouse device section, add:
```

Option "ZAxisMapping" "4 5"

```

Native Linux apps (why aren't you using Linux Quake 3?) don't need that for the Intellimouse driver, but Cedega and Wine do.

---

### Post by michealm on 2005-04-21
I have that , and do use linux native Q3 now, but when in Cedega or Point to Play i have no access for my scroll

---

