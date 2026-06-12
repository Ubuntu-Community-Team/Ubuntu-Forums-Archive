---
title: "Open Arena issue"
date: 2007-01-18
forum: Gaming &amp; Leisure
---

### Post by chrisjpb on 2007-01-18
I jsut spent the last two hours trying to get open arena installed until i found the pre-compiled version on getdeb. Now i have it installed but if i click on open arena in the games menu a window comes up that says starting open arena, and i get the busy cursor but after a few seconds it just disappears any nothing happens. Any ideas? i hate to think i just wasted this much time

---

### Post by pay on 2007-01-18
Do you have 3d acceleration from your video driver? ```
glxinfo | grep direct
```

---

### Post by lamego on 2007-01-18
Try to run it from the terminal with:
```
/usr/share/openarena/ioquake3.i386
```
Hopefully it will report some error.

---

