---
title: "How to find out what Update Manager last installed."
date: 2009-06-22
forum: General Help
---

### Post by frOOgz on 2009-06-22
Is there a way to find out what the Update Manager last installed. My last update has cured a problem that I have been having with my graphics card.  I would like to investigate this and add some information to some of my previous posts.

---

### Post by michy99 on 2009-06-22
Try looking at```
/var/log/apt/term.log
```You will have to access it with sudo.

---

### Post by geirha on 2009-06-22
or /var/log/dpkg.log

```
grep 'status installed' /var/log/dpkg.log
```

---

### Post by frOOgz on 2009-06-22
Thanks these are both useful.

---

