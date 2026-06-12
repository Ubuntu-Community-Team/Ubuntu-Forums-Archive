---
title: "stripping spaces from find output"
date: 2009-02-18
forum: General Help
---

### Post by dunkyp on 2009-02-18
is it possible to replace the literal spaces output by find with slashes so I can pipe the outputted names of files with spaces in their filename??

---

### Post by sdennie on 2009-02-18
This will print the contents of every file matching *foo* even if they have spaces in their names:

```

find . -type f -name "*foo*" -print0 | xargs -0 cat

```

Hope that helps.

---

### Post by dunkyp on 2009-02-18
yeah thanks that's great :D

---

