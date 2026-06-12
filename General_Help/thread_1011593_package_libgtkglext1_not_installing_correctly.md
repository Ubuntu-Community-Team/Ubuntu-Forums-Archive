---
title: "package libgtkglext1 not installing correctly"
date: 2008-12-14
forum: General Help
---

### Post by nahanchi on 2008-12-14
When I try to run pSX, I get the following message:

./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

So I ran **locate libgtkglext**, which came up blank.

I then ran **sudo apt-get install libgtkglext1**, which ran successfully, but locate still turned up empty.

I then ran **sudo apt-get install libgtkglext1-dev**, which ran successfully, but locate still turned up empty.

Does anyone know how to fix this?  I am running Hardy on an AMD64.

Thanks in advanced

---

### Post by sedawk on 2008-12-14
I found the file doing this (first locating the package
and then listing the content of the package)

```

>dpkg -l |grep libgtkgl
...
>dpkg -L libgtkglext1
...
/usr/lib/libgdkglext-x11-1.0.so.0
/usr/lib/libgtkglext-x11-1.0.so.0
>

```

The tool "locate" works so fast, because it uses a fast database instead
of examining the file system. So recent changes to the file systems
are not seen by locate until you call "updatedb" before.

---

### Post by nahanchi on 2008-12-15
Thanks, sedawk.

I was really hoping against hope that the version of pSX I downloaded was 64-bit, but I guess not.

---

