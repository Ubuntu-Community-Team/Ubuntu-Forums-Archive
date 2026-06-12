---
title: "gimp batch-mode"
date: 2012-10-26
forum: Desktop Environments
---

### Post by konze on 2012-10-26
Hello,

I've tried to use the gimp batch-mode. I've followed this instruction over here [(click me)]("http://www.gimp.org/tutorials/Basic_Batch/").

When I type the command:
```
gimp -i -b '(simple-unsharp-mask "foo.png" 5.0 0.5 0)' -b '(gimp-quit 0)'
```
I get the following errors:
```
/usr/lib/gimp/2.0/plug-ins/scangearmp: error while loading shared libraries: libgimp-2.0.so.0: wrong ELF class: ELFCLASS64

(gimp:31160): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
batch command executed successfully

```

How can I solve this problem?

Best regards

konze

---

