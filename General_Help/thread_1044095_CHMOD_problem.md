---
title: "CHMOD problem"
date: 2009-01-19
forum: General Help
---

### Post by beeja on 2009-01-19
Dear All,

By mistake, as root I had changed the permission of chmod to 600 uysing chmod commann. Now I am unable to execute chmod to change it previous state. How can I do this again. Pleas help me.

---

### Post by adamlau on 2009-01-19
Fast and easy way would be to boot into live media and: 

```
chmod 755 /path/to/mounted/bin/chmod
```

---

### Post by snkiz on 2009-01-19
second that

---

