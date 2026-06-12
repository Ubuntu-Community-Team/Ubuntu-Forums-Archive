---
title: "A quesion with &quot;ps -aux&quot;"
date: 2009-05-25
forum: General Help
---

### Post by colau on 2009-05-25
```

ps -aux

``````

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root        22  0.0  0.0      0     0 ?        S<   May25   0:00 [ata/0]
root      2363  0.0  0.0   1808   524 tty4     Ss+  May25   0:00 /sbin/getty 384
root      2859  0.0  0.2  17508  2684 ?        Ssl  May25   0:00 /usr/sbin/conso
root      3329  4.5  4.0  83568 41172 tty7     Rs+  May25   2:20 /usr/X11R6/bin/
111       3201  0.0  0.4   6664  4368 ?        Ss   May25   0:00 /usr/sbin/hald

```

What does it mean by
1. S<
2. Ss+
3. Ssl
4. Rs+
5. tt4
6. tt7
7. Ss
8. VSZ
9. RSS

Last row what kind of user "111" it is?

---

### Post by kidders on 2009-05-26
Hi there,[LIST=1]
[*]S< - High priority, sleeping
[*]Ss+ - Foreground process, session leader, sleeping
[*]Ssl - Multi-threaded, session leader, sleeping
[*]Rs+ - Foreground process, session leader, running
[*]tty4 - Process attached to terminal tty4
[*]tty7 - Process attached to terminal tty7
[*]Ss - Session leader, sleeping
[*]VSZ - Virtual memory SiZe
[*]RSS - Resident Set Size
[/LIST]

> **colau said:**
> Last row what kind of user "111" it is?ps can't establish the name for that user ... it's probably "hal".

I hope that helps. Take a look at ps's man page for more complete information about its output.

---

### Post by colau on 2009-05-27
Thanks.

---

