---
title: "quake 4 not detecting dual cores"
date: 2008-02-08
forum: Gaming &amp; Leisure
---

### Post by rajeev1204 on 2008-02-08
Hi

I have an AMD dual core processor which is detected by the system.

uname -a says kernel #2 SMP on x86_64

System monitor shows 2 CPUS


But the new quake 4 patch which has support for dual core doesnt detect it.

any ideas?


regards

rajeev


oops solved it. Had to use quake4-smp as command to run the game.:D

---

### Post by Sockerdrickan on 2008-02-08
Also use
```
r_useSMP 1
```

---

