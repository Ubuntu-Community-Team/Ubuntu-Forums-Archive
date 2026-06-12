---
title: "having trouble compiling sylpheed-claws cvs"
date: 2006-04-16
forum: Desktop Environments
---

### Post by russellc on 2006-04-16
i'm having a bit of an error trying to compile the sylpheed-claws cvs. maybe i'm missing something? i tried searching and didn't really come up with much. i have installed flex and previously i worked out an error with bison (some yacc error) from a little bit of searching in google. so, to make it simple, yes, i have tried and i would be quite grateful if anyone can help me out with this error :)

```
/bin/sh ../config/ylwrap matcher_parser_lex.l .c matcher_parser_lex.c -- /bin/sh /home/russellc/CVS/sylpheed-claws/config/missing --run flex
make[4]: *** [matcher_parser_lex.c] Error 1
make[4]: Leaving directory `/home/russellc/CVS/sylpheed-claws/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/russellc/CVS/sylpheed-claws/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/russellc/CVS/sylpheed-claws/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/russellc/CVS/sylpheed-claws'
make: *** [all] Error 2

```

so that's the error i get during the make command. i'm using dapper, but i don't think that is really relavant (which is why i posted here). if this is the wrong place, then could a mod please move it to the right place? thanks! :)

---

### Post by hw-tph on 2006-04-16
I haven't built this package so I cannot really comment with any authority, but did you follow the instructions? Did the cvs checkout include an autogen.sh script, and if so - did you run it?


Håkan

---

### Post by colinleroy on 2006-04-16
If you installed flex and/or bison *after* you tried to build sylpheed-claws for the first time, restart all the process for sylpheed-claws: ./autogen.sh && make && sudo make install. This should work better...

---

