---
title: "Can not find library"
date: 2014-04-19
forum: Gaming &amp; Leisure
---

### Post by jaker2 on 2014-04-19
Hello, I have a problem when I compile my kernel always in 100% throws this error and which perhaps I tried to reinstall all programs and libraries in the system have .. and still nothing .. therefore appeal to you ..

```
/usr/bin/ld: cannot find -lncursescollect2: error: ld returned 1 exit status
make[2]: *** [src/server/worldserver/worldserver] Error 1
make[1]: *** [src/server/worldserver/CMakeFiles/worldserver.dir/all] Error 2
make: *** [all] Error 2
```

Thank you in advance for your answer

---

### Post by steeldriver on 2014-04-19
Hello and welcome to the forums

Not sure I understand why a kernel build would require ncurses, however the library you need is probably provided by the package libncurses5-dev

You may also need libncurses**w**5-dev (for wide character support)

---

