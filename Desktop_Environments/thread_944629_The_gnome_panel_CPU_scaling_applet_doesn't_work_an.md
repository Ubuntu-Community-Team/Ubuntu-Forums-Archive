---
title: "The gnome panel CPU scaling applet doesn't work anymore"
date: 2008-10-11
forum: Desktop Environments
---

### Post by ZankerH on 2008-10-11
I've recently re-installed ubuntu on my laptop, and it appears I've somehow lost the fonctionality of the CPU scaling applet: it displays the current frequency, but I can't get the menu to display by left-clicking on it. The CPU frequency does scale (it appears to be on "on-demand" mode"), but I can't set it manually. There is no issue with left-clicking any of the other panel items.

Could anyone help me pinpoint the source of this problem?

---

### Post by Yellow Pasque on 2008-10-11
Most likely, you don't have cpufrequtils installed.
```
sudo apt-get install cpufrequtils
```

---

### Post by Ocxic on 2008-10-11
sudo chmod +s /usr/bin/cpufreq-selector will let the applet do it's thing.

---

