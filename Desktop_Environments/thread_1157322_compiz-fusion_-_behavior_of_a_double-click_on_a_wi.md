---
title: "compiz-fusion - behavior of a double-click on a window title bar"
date: 2009-05-12
forum: Desktop Environments
---

### Post by graysky on 2009-05-12
Currently, when I double-click on a Window's title bar using compiz-fusion, it will just roll up and roll down.  I'd like it to cause the window to maximize and then when double-clicked again, reduce the size to whatever it was prior to the maximization.  I can't find an option for this.  Anyone?

---

### Post by uupreti on 2009-05-12
> **graysky said:**
> Currently, when I double-click on a Window's title bar using compiz-fusion, it will just roll up and roll down.  I'd like it to cause the window to maximize and then when double-clicked again, reduce the size to whatever it was prior to the maximization.  I can't find an option for this.  Anyone?


You can go to **System->Preferences-> Windows** and then change to **Titlebar action** to whatever you want when you click on that bar.

---

### Post by graysky on 2009-05-12
> **uupreti said:**
> You can go to **System->Preferences-> Windows** and then change to **Titlebar action** to whatever you want when you click on that bar.

I don't think that works for compiz-fusion though...

```
Cannot start the preferences application for your window manager

Window manager "compiz" has not registered a configuration tool
```

---

### Post by Oracle_The_Blind on 2009-07-07
In case you're still looking, I've just had the same problem and have found the solution here:
[http://ubuntuforums.org/showthread.php?t=229871](http://ubuntuforums.org/showthread.php?t=229871)

What you need to do is:
System -> Preferences -> Emerald Theme Manager -> Emerald Settings
Then change the value of Titlebar Double-Click Action from "Shade" to "Maximize/Restore"

---

