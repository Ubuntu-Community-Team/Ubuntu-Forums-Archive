---
title: "Solution: restore deleted network icon in panel (Lubuntu)"
date: 2012-07-18
forum: Desktop Environments
---

### Post by cogitordi on 2012-07-18
If you have deleted the network icon from the taskbar panel, you can restore it by doing the following:

= use your editor (leafpad) to open "~/.config/lxpanel/Lubuntu/panels/panel"

= add the following *before* "Plugin { type = dclock" :

```
Plugin {
    type = tray
}
```

= close your session (log out) and start a new session (log in)

---

