---
title: "Memory usage in the top output, sth wrong"
date: 2006-09-26
forum: Desktop Environments
---

### Post by utab on 2006-09-26
Dear all,

Memory output on the top output is like the one below, it seems that most of that is being used or i am mistaken

Mem:   1035972k total,  1023380k used,    12592k free,     5872k buffers

What can be the problem? I have come with this problem because my thunderbird nearly takes 20 seconds to open and i am experiencing some performance problems even in the simple shell commands.

Best regards,

---

### Post by fstab on 2006-09-26
Use free command to check memory usage...

```

[FONT="Fixedsys"]
user@pago:~$ free -m
                  total       used       free     shared    buffers     cached
Mem:           694        685          8          0        142        308
-/+ buffers/cache:        234        459
Swap:         1576          0       1576[/FONT]
```


The line that starts with -/+ is the *real* memory usage in MB.

---

