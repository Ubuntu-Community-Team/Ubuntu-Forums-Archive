---
title: "How to remove MAC theme completely and revert to human"
date: 2009-12-18
forum: Desktop Environments
---

### Post by haribol707 on 2009-12-18
hello, I followed one of the instructions on this forum to install mac4lin theme and a few other utilities (fonts/icons/awn/cairo) to turn my desktop into Mac. Now, I am trying to revert to old settings. I was able to remove the Mac4lin theme from Emerald but still the buttons on window title are placed on the wrong side as in a Mac. How do I reset everything to default setting?

---

### Post by howefield on 2009-12-18
> **haribol707 said:**
> ..but still the buttons on window title are placed on the wrong side as in a Mac.

Open a terminal and type 

```
gconf-editor
```

Navigate to apps\metacity\general and look for button layout.

You want it to read, menu:minimize,maximize,close

which I guess is the opposite to what it is reading for you right now.

gconf-editor is quite a useful application to have on your menu, if you want to open it up via your Applications menu, go to System > Preferences > Main Menu and click on System tools and check Configuration Editor. It will now show as a menu item under Applications > System Tools > Configuration Editor.

---

### Post by spiderbatdad on 2009-12-18
Usually the install directory of mac4lin also contains an uninstall script.

---

### Post by haribol707 on 2009-12-21
Thanks! UnInstall script from Mac4Lin directory did the trick :)

---

### Post by KRISHNASHK on 2012-02-01
> **haribol707 said:**
> Thanks! UnInstall script from Mac4Lin directory did the trick :)
how about macbuntu, if i install it will i be able to remove it completely

---

### Post by KRISHNASHK on 2012-02-01
> **spiderbatdad said:**
> Usually the install directory of mac4lin also contains an uninstall script.
how about macbuntu, if i install it will i be able to remove it completely

---

