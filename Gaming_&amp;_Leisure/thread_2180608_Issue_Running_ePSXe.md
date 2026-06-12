---
title: "Issue Running ePSXe"
date: 2013-10-13
forum: Gaming &amp; Leisure
---

### Post by samuel-brockmann on 2013-10-13
I'm trying to run ePSXe. When I type the command to run it, I get the following error message:
```
error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

So, how do I get libgtk-1.2.so.0?


I tried creating a symbolic link like so: 
```
ln -s /usr/lib/gtk-3.0 /usr/lib/libtgk-1.2.so.0
```

Unfortunately, I got a "permission denied" error, and gtk-3.0 isn't something that can have permissions edited. 

So, how can I get ePSXe to run?

---

