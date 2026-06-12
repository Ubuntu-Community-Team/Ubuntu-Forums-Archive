---
title: "GNome - stop Files window from opening maximized"
date: 2022-01-01
forum: Desktop Environments
---

### Post by uacnt83982803 on 2022-01-01
This truly drives me insane - the Files application always opens maximized.  I can't stand this... I checked everything in Settings, nothing found.  I installed gnome tweaks, nothing there either.  And as far as I can tell there isn't any option within the Files application itself to control this.

Is there a fix?

---

### Post by KBar on 2022-01-01
```
gsettings set org.gnome.mutter auto-maximize false
```

---

### Post by vanadium on 2022-01-02
KBar may be on the right track in what happened with you. If a window has a large size as such, it will automatically be maximized. Alternatively, unmaximize and resize the window to a quite smaller size, then close the window. Next time, nautilus will start with the smaller sized window, which will not be automaximized.

---

