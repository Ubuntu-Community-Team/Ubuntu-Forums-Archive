---
title: "why I have to remove ubuntu-desktop in order to install tpd?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by baosheng on 2006-08-29
I wanna install a software called tpd that enables me to use IBM Thinkpad special keys. 

But the synaptic said if I wanna install tpd, ubuntu-desktop will be removed. 
How can this happen?

What can I do to deal this problem?

---

### Post by meng on 2006-08-29
I'm guessing that tpd replaces (and therefore requires removal of) another package that is part of the ubuntu-desktop metapackage (bundle). In order to remove that other package, you have to remove the metapackage. But that's fine because the metapackage is just like an empty wrapper. It makes for a convenient way of installing a huge load of packages, but the metapackage itself can be removed subsequently without harm.

---

### Post by glotz on 2006-08-29
I remember wondering about similar issue in the past. I think that this should be changed. The meta package is handy instead of manual labor but why does the default install must use it?

---

### Post by meng on 2006-08-29
Actually you have a good point I think. Even easier would be if the default install used it, then uninstalled the metapackage.

---

### Post by glotz on 2006-08-29
True! :)

---

