---
title: "[SOLVED] Some compiz plugins work, some not"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by orbital on 2007-09-13
I have Wobbly Windows and some other plugins working fine but for some reason Desktop Cube is not working at all. And Expo only shows one desktop (used to show all four of them lined side by side). Any idea how to get these working again?

---

### Post by praet on 2007-09-13
check that your workspaces are configured correctly.

System > Preferences > CompizConfig Settings manager
Goto General Options, Desktop Size tab, and change 
desktops = 1
horizontal size = 4
vertical size = 1

If the changes are not made automatically, then restart compiz ```
compiz --replace
```

---

### Post by orbital on 2007-09-13
Thanks, everything works ok again.

---

### Post by praet on 2007-09-13
great!

---

