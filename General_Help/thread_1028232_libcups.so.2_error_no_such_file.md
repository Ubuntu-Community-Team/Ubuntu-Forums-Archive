---
title: "libcups.so.2 error no such file"
date: 2009-01-02
forum: General Help
---

### Post by Arenlor on 2009-01-02
arenlor@Charlie:/usr/lib/cups/filter$ ./rastertoz600
./rastertoz600: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory
arenlor@Charlie:/usr/lib/cups/filter$ sudo ./rastertoz600
[sudo] password for arenlor: 
./rastertoz600: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory
arenlor@Charlie:/usr/lib/cups/filter$ ls -l /usr/lib/libcups.so.2
-rw-r--r-- 1 root root 232392 2008-12-21 08:19 /usr/lib/libcups.so.2

I don't get it, do I need to chmod it or something?

---

### Post by prapanjganeshan on 2011-03-09
check this

[http://ubuntuforums.org/showthread.php?p=10540039#post10540039](http://ubuntuforums.org/showthread.php?p=10540039#post10540039)

---

