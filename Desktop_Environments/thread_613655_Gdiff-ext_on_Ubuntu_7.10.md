---
title: "Gdiff-ext on Ubuntu 7.10"
date: 2007-11-15
forum: Desktop Environments
---

### Post by mdecandia on 2007-11-15
Hi all,
I've installed  diff-ext_0.2.3-1_i386.deb (for ubuntu Hardy) and nautilus crashes on starting.
Anybody has experience in this?

Thanks,
Michele

---

### Post by mdecandia on 2007-11-16
I've resolved fixing missing theme icon. After installation:

1. launch gconf-editor
2. see if key /apps/diff-ext/icons has value diff-ext; if it does not, set it to diff-ext 

Bye

---

