---
title: "Problem with Adobe Reader"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Guybrush84 on 2006-07-14
Hi!

I downloaded Adobe Reader from Adobe's web site and installed it, but when I try to launch it I receive an error:

```
error while loading shared libraries: libgdk_pixbuf_xlib-2.0.so.0: cannot open shared object file: No such file or directory
```

So i tried with:

```
find / -iname libgdk_pixbuf_xlib-2.0.so.0
/usr/lib/libgdk_pixbuf_xlib-2.0.so.0
```

I created the file ld.so.conf in /etc and i wrote "/usr/lib" in it, then i   tried with:

```
export LD_LIBRARY_PATH=/usr/lib
```

But the program won't start. What can I do?

Thanks a lot!

---

### Post by jordilin on 2006-07-14
Why not try to install Adobe Reader from synaptic?

---

### Post by stoffepojken on 2006-07-14
Evince?

---

