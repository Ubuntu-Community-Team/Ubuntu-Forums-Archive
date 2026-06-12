---
title: "Disabling windows from being snapped to edges"
date: 2019-02-02
forum: Desktop Environments
---

### Post by lowprofile2 on 2019-02-02
As title reads, i want to be able to disable the edge snapping feature i find it annoying. I like to auto hide my task bar and stretch the current window to fill up the screen without full screening it. i am on version 18.04.1

---

### Post by vanadium on 2019-02-02
Turn edge tiling off with the command
```

gsettings set org.gnome.mutter edge-tiling false

```
If that is not enough, also set org.gnome.shell.overrides to false (similar command). To reset to default, replace "set" by "reset" and omit the last argument.

As I see you are rather new, some extra info. To easily maximize a window, you may want to click the maximize window button. Alternatively, press <Super>+<Up arrow>, or <Alf+F10>. All these methods are by far faster to maximize your window than attempting to drag and resize with the mouse over and over again. These methods do not interfere with edge-tiling, so eventually, this change in habit may lead you to leave that on.

---

