---
title: "UT2004 won't start"
date: 2010-03-04
forum: Gaming &amp; Leisure
---

### Post by wolfyking2 on 2010-03-04
So, I installed ut2004 from the windows disk, and installed the rest using loki's linux installer.  I patched it up to 3369.  When I put the ut2004-bin in the terminal, this is what I get 

```
/home/user/Ut2004/ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory
```

what does this mean?

---

### Post by Brebs on 2010-03-04
Too lazy to search the forums yourself, eh?

ln -sfn /usr/lib/libopenal.so.1 /opt/ut2004/System/openal.so
ln -sfn /usr/lib/libSDL-1.2.so.0 /opt/ut2004/System/libSDL-1.2.so.0

For you, replace /opt/ut2004 by /home/user/Ut2004

The Loki installer should really be doing this itself - I suggest you file a bug report with them.

---

