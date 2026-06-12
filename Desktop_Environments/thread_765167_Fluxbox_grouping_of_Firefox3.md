---
title: "Fluxbox grouping of Firefox3"
date: 2008-04-24
forum: Desktop Environments
---

### Post by Gorgamel on 2008-04-24
When upgrading to new Ubuntu, I noticed that Firefox did not group up (use tabs) anymore when opening more windows.
It used to be to write 'gecko' in the group file, but I have tried firefox, Firefox, firefox-3.0, but nothing works.

Anyone have any idea what to do/write to make this work again ??

---

### Post by pyronaut on 2008-07-10
in a terminal  type this
    xprop |awk '/WM_CLASS/{print $4}'
 then u'll see a pointer that u click on the title bar of firefox and it should give you the name to put in your groups file

---

### Post by kerry_s on 2008-07-10
```
firefox-bin
```

---

