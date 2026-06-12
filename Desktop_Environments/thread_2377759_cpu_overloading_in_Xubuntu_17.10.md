---
title: "cpu overloading in Xubuntu 17.10"
date: 2017-11-16
forum: Desktop Environments
---

### Post by arpad2 on 2017-11-16
I am experiencing overloaded cpu, while the Task Manager can't show any process which would overloading the system, is this an OS bug?

---

### Post by vasa1 on 2017-11-16
There's something odd there :(

The graph doesn't match the table!

Could you try```
top -n 1 -o %CPU | head -30
```

---

