---
title: "How to Change Fixed Menu Bar"
date: 2011-10-18
forum: Desktop Environments
---

### Post by hoodedperson70 on 2011-10-18
Hi,

I was wondering if there's any way to keep the menu bar within each window, instead of being fixed at the top. Sorry if this is an easy fix, I don't know much about configuring these things and honestly couldn't find anything when searching.

Thanks!

---

### Post by ubu_dynamite on 2011-10-18
Removing every package containing appmenu and globalmenu does wonders.

```
sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt firefox-globalmenu indicator-appmenu thunderbird-globalmenu
```

---

### Post by hoodedperson70 on 2011-10-18
You are absolutely right, thank you so much!

---

