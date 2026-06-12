---
title: "how to copy folder leaving out hidden files"
date: 2010-12-18
forum: Desktop Environments
---

### Post by peterthewolf on 2010-12-18
Title just about says it.

Input folder has test.txt .test1.tx and many other files with various names.

How can I copy all the unhidden files to a new folder.

---

### Post by clrg on 2010-12-18
Why don't you try ```
cp -ripv /source/folder/* /target/folder 
```

---

### Post by peterthewolf on 2010-12-18
Thank you that worked fine.

---

