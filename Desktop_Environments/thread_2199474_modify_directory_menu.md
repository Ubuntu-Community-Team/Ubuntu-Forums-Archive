---
title: "modify directory menu"
date: 2014-01-14
forum: Desktop Environments
---

### Post by Previous1 on 2014-01-14
After a reinstall of Xubuntu 12.04, I have a typo in the directory menu (an unwanted underscore). The menu plugin is mentioned in /usr/share/xfce4/panel/plugins/directorymenu.desktop, where it refers to

```
Type=X-XFCE-PanelPlugin
X-XFCE-Module=directorymenu
X-XFCE-Internal=TRUE
```

Further I've found entries in xfce4-panel.xml, which control the directory and pattern. How could I fix the typo?

---

### Post by Buntu Bunny on 2014-01-14
You could try it graphically. Applications Menu > Settings > Main Menu, then select the problem entry, hit "properties", and edit the name there.

---

### Post by Previous1 on 2014-01-14
My image is a bit unclear, with directory menu I meant this one:

[http://docs.xfce.org/xfce/xfce4-panel/directorymenu](http://docs.xfce.org/xfce/xfce4-panel/directorymenu)

---

