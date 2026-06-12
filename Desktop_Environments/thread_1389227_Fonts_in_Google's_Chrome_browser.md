---
title: "Fonts in Google's Chrome browser"
date: 2010-01-24
forum: Desktop Environments
---

### Post by Linuxgood on 2010-01-24
Hi!

Which fonts do you use ? The default looks really ugly, at
least on my computer.

---

### Post by pickarooney on 2010-03-25
They look rotten on mine too. I won't bother using their brower until they supprot system anti-aliasing.

---

### Post by krismatth3 on 2010-03-26
[http://code.google.com/p/chromium/issues/detail?id=13185]("http://code.google.com/p/chromium/issues/detail?id=13185")

A known problem, and on the desiredata (what a name) list. Guess we just have to wait. :-(

---

### Post by falconindy on 2010-03-26
Add anti-aliasing to your ~/.Xdefaults file:

```
Xft.antialias: true
```

Fonts are now "pretty" in Chromium.

---

