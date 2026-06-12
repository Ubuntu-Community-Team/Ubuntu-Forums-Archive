---
title: "how to compare two directory?"
date: 2009-02-09
forum: General Help
---

### Post by siuchi on 2009-02-09
Hi all,

I have two directory which is almost the same. but there would be one files that is different.

Is there any way that i can quickly compare these two directory , include its sub-directory, and all files include these two directory and find out which which file is different.

Mang many of thanks

---

### Post by geirha on 2009-02-09
```
diff -r -u dir1/ dir2/
```

---

