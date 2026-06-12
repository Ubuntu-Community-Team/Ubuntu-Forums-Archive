---
title: "How can I change Terminal tab names with the command line"
date: 2009-01-21
forum: Desktop Environments
---

### Post by tbttfox on 2009-01-21
I've found many places that tell you how to change tab names in KDE with dcop, but I can't find any info on doing it within xfce.

Can anybody point me in the right direction?

Thanks!

---

### Post by mali2297 on 2009-01-21
Try
```

echo -ne "\e]2; tab name\a"

```
Change 'tab name' to whatever you like.

---

### Post by tbttfox on 2009-01-22
I do apologize ... this is tcsh

The only thing that happens is I get "-ne" echoed back.

---

