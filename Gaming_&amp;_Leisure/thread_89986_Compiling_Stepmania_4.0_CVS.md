---
title: "Compiling Stepmania 4.0 CVS"
date: 2005-11-13
forum: Gaming &amp; Leisure
---

### Post by chesster on 2005-11-13
Hello,

Is there anyone who has experience building stepmania cvs on ubuntu?  Every time I try to configure the code, this message pops out in my console:

```
./configure: line 8176: AC_LIB_PREPARE_PREFIX: command not found
./configure: line 8177: AC_LIB_RPATH: command not found
./configure: line 8182: syntax error near unexpected token `iconv'
./configure: line 8182: `      AC_LIB_LINKFLAGS_BODY(iconv)'
```

Is there any workaround/fix for this?  Thanks.

---

### Post by oskude on 2005-11-14
seems that youre missing a library, dunno what...
have u installed all *-dev packages that stepmania depends on...
read the readme, install, etc. files that came with it...
for better help you should search/ask this kind of things on their forum/mailing-list...

---

