---
title: "How do I do...?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by arctu on 2006-06-03
I have read it somewhere that after we compile something from source there is another command instead of make install that make the thing we compile appear in the package database. What is the command?

---

### Post by Jussi Kukkonen on 2006-06-03
Couple of choices here. 

1. If you've downloaded sources for Ubuntu or debian you can just *dpkg-buildpackage*.

2. otherwise you want *checkinstall -D*

---

