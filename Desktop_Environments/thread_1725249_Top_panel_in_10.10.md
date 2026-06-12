---
title: "Top panel in 10.10"
date: 2011-04-09
forum: Desktop Environments
---

### Post by mdhollis on 2011-04-09
Can someone please help me revert my desktop settings to default.  I removed evolution from the top right panel and I can't get the original launcher in the panel back.  I'm running 10.10.

---

### Post by quesadilla on 2011-04-09
just right click on the panel and hit "add to panel". you can also drag icons from the menu onto the panel and they will appear

---

### Post by Frogs Hair on 2011-04-09
Try this to restore panel to defaults.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by mdhollis on 2011-04-09
> **Frogs Hair said:**
> Try this to restore panel to defaults.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

Thanks!

---

### Post by Frogs Hair on 2011-04-09
> **mdhollis said:**
> Thanks!

You're Welcome

---

### Post by fatal_ERROR777 on 2011-04-10
Worked for me either! Thank you.

---

