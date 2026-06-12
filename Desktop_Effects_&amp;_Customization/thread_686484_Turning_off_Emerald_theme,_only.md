---
title: "Turning off Emerald theme, only"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by japtar10101 on 2008-02-03
N00b question, but how do I turn off Emerald theme WITHOUT turning off Compiz Fusion?  
Thank you for your time.

---

### Post by FuturePilot on 2008-02-03
```
gtk-window-decorator --replace
```

---

### Post by ajgreeny on 2008-02-03
I think you just chose another theme from the System>Preferences>Appearance in the menu.  I don't even have emerald installed and compiz-fusion still runs great.

---

### Post by japtar10101 on 2008-02-03
> **FuturePilot said:**
> ```
gtk-window-decorator --replace
```

When I do that, the whole window decoration disappears.  I can't close my windows without using the menu bar...

---

### Post by DaymItzJack on 2008-02-03
Alt+F4

---

### Post by Tenken on 2008-02-03
You could try this commands to stop emerald and start metacity (the default gnome window manager)

```
killall emerald
metacity --replace
```

---

### Post by japtar10101 on 2008-02-03
> **Tenken said:**
> You could try this commands to stop emerald and start metacity (the default gnome window manager)

```
killall emerald
metacity --replace
```
Nope...
I guess I should just uninstall emerald

---

