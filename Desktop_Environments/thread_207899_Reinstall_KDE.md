---
title: "Reinstall KDE"
date: 2006-07-02
forum: Desktop Environments
---

### Post by mjs on 2006-07-02
Hi,

What am I need to do for reinstall the KDE's window manager?

When I open an application in the KDE, the title bar (that where the button close is ), don't exists.

In the gnome all works very well.

Thanks

---

### Post by louis_nichols on 2006-07-02
you should reinstall the package kubuntu-desktop. easiest way, from synaptic. just search it, right click and choose reinstall.

---

### Post by aysiu on 2006-07-02
I don't think reinstalling KDE will solve your issue. It sounds like some kind of theme corruption or something.

This may help: ```
mv ~/.kde ~/.kde.backup
```

---

### Post by Jucato on 2006-07-02
you could also try to change the window decoration, as I think it's the one giving the problem.
System Settings > Appearance > Window Decorations > change it to something else (don't forget to click Apply).

It could also be possible that *kwin* is not running. Press Ctrl+Esc and check if it is there. If it's not, Press Alt+F2 and type in *kwin*

Hope that helps

---

