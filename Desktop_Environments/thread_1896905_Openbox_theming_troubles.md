---
title: "Openbox theming troubles"
date: 2011-12-18
forum: Desktop Environments
---

### Post by jfreak_ on 2011-12-18
So I did a vanilla openbox on ubuntu. Set the theme using lxappearance but only firefox and pcmanfm are obeying the set theme, rest are some sort of windows 98 classic theme. What to do?:confused:

---

### Post by LarsKongo on 2011-12-18
The other apps must be GTK3 then. Pcmanfm is a GTK2 app. Lxappearance doesn't change the GTK3 theme.

So if you want to use the Ambiance GTK theme (for exmaple) on a minimal install you'll have to do this:

Terminal:

1. sudo apt-get install gtk3-engines-unico light-themes

2. nano ~/.config/gtk-3.0/settings.ini

Add this:
```
[Settings]
gtk-theme-name = Ambiance
```

---

### Post by jfreak_ on 2011-12-18
Thanks. It worked.

---

