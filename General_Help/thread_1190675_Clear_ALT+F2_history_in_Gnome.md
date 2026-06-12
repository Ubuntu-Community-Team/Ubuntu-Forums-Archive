---
title: "Clear ALT+F2 history in Gnome"
date: 2009-06-18
forum: General Help
---

### Post by cviorel on 2009-06-18
Use this command in your terminal to clear the “Run Program” dialogue box invoked by ALT+F2 in Gnome:
```
gconftool-2 --set /apps/gnome-settings/gnome-panel/history-gnome-run --type list --list-type string "[]"
```

---

