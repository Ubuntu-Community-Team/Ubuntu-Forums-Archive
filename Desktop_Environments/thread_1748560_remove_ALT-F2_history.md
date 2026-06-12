---
title: "remove ALT-F2 history"
date: 2011-05-03
forum: Desktop Environments
---

### Post by cccc on 2011-05-03
Hi

I have ubuntu 10.04 and am running gnome desktop
Howto remove  ALT-F2 history?

---

### Post by cccc on 2011-05-03
```

# gconftool-2 --set /apps/gnome-settings/gnome-panel/history-gnome-run --type list --list-type string "[]"
```should clear ALT+F2 history.

---

### Post by sisco311 on 2011-05-03
EDIT: cccc beat me to it. :)

You have to clear the /apps/gnome-settings/gnome-panel/history-gnome-run gconf key. You can use gconf-editor (a GUI app) or run:
```
gconftool-2 --set /apps/gnome-settings/gnome-panel/history-gnome-run --type list --list-type string "[]"
```

---

