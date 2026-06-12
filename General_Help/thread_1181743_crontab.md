---
title: "crontab"
date: 2009-06-08
forum: General Help
---

### Post by jspolen on 2009-06-08
Hi just wondering if this is a valid crontab entry, I want it to run every fourth hour.

* 2,6,10,14,18,22 * * * root <my command>

---

### Post by iponeverything on 2009-06-08
its valid.

```
* 0-23/4 * * * root cmd 

```

Will also work.

---

