---
title: "how not to show directories with ls?"
date: 2009-04-21
forum: General Help
---

### Post by fduff on 2009-04-21
in some linux folders it may be useful to hides subfolders from a directory and only show its files.

```
ls --hide=PATTERN
```

might do the trick, but I havent figure out what PATTERN is supposed to be!

any idea?

---

### Post by James_Lochhead on 2009-04-21
*/ I think. That means anything that doesn't end with a / (directories).

---

### Post by James_Lochhead on 2009-04-21
No, that doesn't seem to work.

---

### Post by mixmaster on 2009-04-21
ls -l | grep -v "^d"

---

### Post by fduff on 2009-04-21
thanks for that!

```
ls -l | grep -v "^d"
```

*there's a space after the* **-v**

---

### Post by regala on 2009-04-21
> **fduff said:**
> thanks for that!


or you can do
```

find . -type f -maxdepth 1

```

---

