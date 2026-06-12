---
title: "Remove application menu icon"
date: 2012-06-02
forum: Desktop Environments
---

### Post by tivatranquio on 2012-06-02
How can I remove the application menu icon from the xfce panel?

---

### Post by brainwash on 2012-06-02
In order to remove the icon you would need to edit the particular source  file, because the application menu plugin simply does not offer a way  (graphical or via configuration file) to hide the selected or default icon:

[http://git.xfce.org/xfce/xfce4-panel/tree/plugins/applicationsmenu/applicationsmenu.c?h=xfce-4.8](http://git.xfce.org/xfce/xfce4-panel/tree/plugins/applicationsmenu/applicationsmenu.c?h=xfce-4.8)

Moreover, you might want to fill a feature request at [https://bugzilla.xfce.org/](https://bugzilla.xfce.org/), so it will get implemented one day.

---

### Post by vasa1 on 2012-06-02
> **tivatranquio said:**
> How can I remove the application menu icon from the xfce panel?

If you're asking just in order to make more space available on the panel, you could rename it to "Apps" and maybe even remove the little rat?

---

### Post by tivatranquio on 2012-06-02
I just want to remove the icon

---

