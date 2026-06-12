---
title: "title bar missing"
date: 2009-03-10
forum: Desktop Environments
---

### Post by jhively56 on 2009-03-10
I had power go out during an update. Now the title bar is missing from all windows.  I saw that entering  "metacity --replace" was recommended for a similar problem in ubuntu. what should I do for xubuntu?

---

### Post by Simian Man on 2009-03-10
Try running:
```
xfwm4 &
```

And see if that does the trick.

---

### Post by jhively56 on 2009-03-10
Simian Man, that did the trick. Thank you very much!

---

