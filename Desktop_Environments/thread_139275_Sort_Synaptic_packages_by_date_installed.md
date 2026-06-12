---
title: "Sort Synaptic packages by date installed?"
date: 2006-03-03
forum: Desktop Environments
---

### Post by rskovacs on 2006-03-03
Hi everyone-

I was wondering if anyone could help me figure out how to generate a list of all installed packages sorted by date installed.  The purpose of this would be for me to have an easier time remembering what packages I would have to reinstall next time I reinstall Ubuntu, because they would be all the packages installed since the date of the last Ubuntu install.  Thanks!

---

### Post by cwaldbieser on 2006-03-03
[QUOTE=rskovacs]Hi everyone-

I was wondering if anyone could help me figure out how to generate a list of all installed packages sorted by date installed.  The purpose of this would be for me to have an easier time remembering what packages I would have to reinstall next time I reinstall Ubuntu, because they would be all the packages installed since the date of the last Ubuntu install.  Thanks![/QUOTE]
Ideally, you should be able to do this with one of the package tools.  I didn't see how to do it by skimming the man pages, though.  If you haven't been clearing out your package cache, the following pipeline might be a starting point:
```

$ ls -l --sort=time --full-time /var/cache/apt/archives | sort -k 6,7 -k 9 | sort -u -k 9 | awk '{print $9, $6;}'

```

---

