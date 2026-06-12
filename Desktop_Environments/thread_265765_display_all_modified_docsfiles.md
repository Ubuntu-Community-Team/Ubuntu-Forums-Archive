---
title: "*** display all modified docs/files ???  ***"
date: 2006-09-26
forum: Desktop Environments
---

### Post by josh on 2006-09-26
hello!

is there a way to list all the documents/files that was created or modified the last time the system was on? thanks!

---

### Post by Ramses de Norre on 2006-09-26
```
find / -mtime n
#or
find / -mmin n

```
In the first command all files are displayed that are modified/created in the last n*24 hours, in the second one all files modified/created in the last n minutes.

---

### Post by josh on 2006-09-26
thanks!

---

