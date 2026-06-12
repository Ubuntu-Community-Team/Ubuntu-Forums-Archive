---
title: "recent update, gaim icon error in gnome-panel"
date: 2006-05-30
forum: Desktop Environments
---

### Post by nojjy on 2006-05-30
After updating Dapper in the last day or two my gaim icon is missing from the gnome panel and I am recieving the following error:

> Could not load icon
Details: Failed to open file '/usr/share/icons/Tangerine/24x24/apps/gaim.png': No such file or directory 
Is this a problem with the tango icon set?  A bug?

---

### Post by johnc4510 on 2006-05-30
I don't know, the update was today I think. It replaced the orange one with a yellow one, more like the old one.

---

### Post by philippe_carlo on 2006-08-03
```
sudo ln -s /usr/share/icons/gnome/24x24/apps/gaim.png /usr/share/icons/Tangerine/24x24/apps/gaim.png
```

---

