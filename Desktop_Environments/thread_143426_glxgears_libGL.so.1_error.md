---
title: "glxgears libGL.so.1 error"
date: 2006-03-12
forum: Desktop Environments
---

### Post by f3tus on 2006-03-12
I was having trouble installing some drivers, so I tried something I came accross, which is:
```

ln -d /usr/share/fglrx/diversions/libGL.so.1.2 /usr/lib/libGL.so.1
and than
ln -s /usr/share/fglrx/diversions/libGL.so.1.2 /usr/lib/libGL.so.1

```
Then I tried to run glxgears and this is the output:
```

glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

I just switched from XP, so I knew I'll mess something up the moment I'll get my hands on linux.

Please help.

Edit:
Fixed...

---

