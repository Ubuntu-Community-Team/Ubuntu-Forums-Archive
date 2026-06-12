---
title: "Unable to run GCCG"
date: 2014-04-21
forum: Gaming &amp; Leisure
---

### Post by henrypaulmadore on 2014-04-21
Trying to get GCCG going. Unable to run this software. Says:

Running ./ccg_client mtg.xml
./ccg_client: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by bapoumba on 2014-04-21
Moved to Gaming.
Here may be ? [http://ubuntuforums.org/showthread.php?t=1503674](http://ubuntuforums.org/showthread.php?t=1503674)

---

### Post by oldrocker99 on 2014-04-21
Try this:

```
sudo apt-get install libsdl-net1.2 libsdl-net1.2-dev
```

When you are compiling source code, and a missing library is mentioned, you need the -dev version of that library.

---

