---
title: "How to change or disable the Super key shortcut?"
date: 2018-11-04
forum: Desktop Environments
---

### Post by Zobeid on 2018-11-04
When I tap and release the left Super key, it brings up my activities.  I want to disable this or change it to some other key combination, so that Super continues to work as a modifier (with other shortcuts) but doesn't do anything by itself.  I'm not finding an obvious way to configure this.  Any suggestions?

---

### Post by vanadium on 2018-11-05
```

gsettings set org.gnome.mutter overlay-key ''

```
or use dconf-editor if you prefer a graphical tool to change the setting.

There currently are two alternative keys for having the overview, Alt+F1 and Super+s. If you still want another key combination, that can be set.

---

### Post by Zobeid on 2018-11-05
Thanks!  This is exactly what I needed.

---

