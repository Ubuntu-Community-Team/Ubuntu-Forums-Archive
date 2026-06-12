---
title: "Messed with Compiz too much"
date: 2011-03-09
forum: Desktop Environments
---

### Post by tumelo on 2011-03-09
I was playing around with compiz too much and kinda messed up some stuff. Is there anyway I can just go back to how stuff was? Without system restore, I don't know of a way I can restore my previous compiz settings.

---

### Post by false truths on 2011-03-09
You can login to safe mode/recovery mode, which disables all visual effects and sets everything to the minimal default. From there you can modify your Compiz to work properly again, then re-enable desktop effects in the appearance controls.

I usually have to do this once a week because of my tweaking efforts.

---

### Post by Copper Bezel on 2011-03-09
If you purge and reinstall the package, it should be reset to default settings. There's also a .compiz in your home folder with configuration settings; erasing that should cause Compiz to start fresh.

---

### Post by stinkeye on 2011-03-09
In the terminal...
```
gconftool-2 --recursive-unset /apps/compiz
```
...will set compiz back to default settings.

---

