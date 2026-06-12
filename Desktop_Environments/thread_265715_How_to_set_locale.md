---
title: "How to set locale?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by pietrob71 on 2006-09-26
This is the output for $locale:
LANG=it_IT.UTF-8
LANGUAGE=it_IT:it:en_GB:en
LC_CTYPE="it_IT.UTF-8"
LC_NUMERIC="it_IT.UTF-8"
LC_TIME="it_IT.UTF-8"
LC_COLLATE="it_IT.UTF-8"
LC_MONETARY="it_IT.UTF-8"
LC_MESSAGES="it_IT.UTF-8"
LC_PAPER="it_IT.UTF-8"
LC_NAME="it_IT.UTF-8"
LC_ADDRESS="it_IT.UTF-8"
LC_TELEPHONE="it_IT.UTF-8"
LC_MEASUREMENT="it_IT.UTF-8"
LC_IDENTIFICATION="it_IT.UTF-8"
LC_ALL=

I would like to set everything to en_GB, for make a test. How can do it?

---

### Post by revertex on 2007-05-03
```
dpkg-reconfigure localeconf
```

---

