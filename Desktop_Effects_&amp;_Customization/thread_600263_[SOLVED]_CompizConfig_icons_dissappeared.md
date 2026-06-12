---
title: "[SOLVED] CompizConfig icons dissappeared"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by dentaku65 on 2007-11-02
Well... today I opened the ccsm and I found that all icons are disappeared.

Anyone have some ideas?

---

### Post by MickS on 2007-11-02
I get the same thing happen when I click on Preferences?

Mick

---

### Post by dentaku65 on 2007-11-02
FIXED!

Due to the missing dependence of librsvg2-common in Compizconfig package the icons are not showed. For KDE users (like me) this is bad because were the package librsvg2-common is installed by default in Gnome env I expecting that the dependence will be solved by CompizConfig in case I don't run a Gnome env.

So to fix this:

```
sudo apt-get install librsvg2-common
```

---

