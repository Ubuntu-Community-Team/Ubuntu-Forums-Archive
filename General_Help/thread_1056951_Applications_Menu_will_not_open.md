---
title: "Applications Menu will not open"
date: 2009-02-01
forum: General Help
---

### Post by icrywolf on 2009-02-01
Applications Menu will not open from the top bar, but Places and System menu's do, Using Intrepid Ibex Ubuntu 

help?

---

### Post by mc4man on 2009-02-01
Open up home folder, (view -> show hidden files if not enabled) and go to .config/menus. Inside is a file applications.menu, delete it and you should be ok.

Or Alt+F2
```
nautilus ~/.config/menus
```

---

