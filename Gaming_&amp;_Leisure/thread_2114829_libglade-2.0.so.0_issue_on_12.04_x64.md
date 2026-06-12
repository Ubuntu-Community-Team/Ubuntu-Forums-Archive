---
title: "libglade-2.0.so.0 issue on 12.04 x64"
date: 2013-02-11
forum: Gaming &amp; Leisure
---

### Post by psxfin on 2013-02-11
I seem to have hit a minor slump here with this library file. The app I'm running is asking for it and after using sudo apt-get install libglade2-0 I'm told I already have the latest version. When I execute the program pSX I'm given this error:

```
./pSX: error while loading shared libraries: libglade-2.0.so.0: cannot open shared object file: No such file or directory
```

I tested this in a VM of 12.10 and it works no problem but my 12.04 desktop keeps throwing off this error. Any suggestion on how I could fix this up? I also tried sudo apt-get install libgtkglext1-dev but it says "is already the newest".

**Edit:**

Sorry but I guess I just didn't dig enough. I found my solution from a post by dfreer from:

[http://ubuntuforums.org/showthread.php?t=394097&page=32](http://ubuntuforums.org/showthread.php?t=394097&page=32)

---

