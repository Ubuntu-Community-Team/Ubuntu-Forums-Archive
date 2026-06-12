---
title: "gconf/QTCreator/static-dynamic lib linking"
date: 2011-03-24
forum: Desktop Environments
---

### Post by ikseg on 2011-03-24
I’ve got really weird problem and don’t know how to resolve it.
      I’ve made the static library. This library contains algorithms for  working with gconf-client. Library works only with using *.so objects. I  wrote full path to each of necessarily *.so files in *.pro file. 



```

LIBS += /home/xray/LibraryLoader/liblibraryloader.a -ldl \
/usr/lib/libgconf2-4/2/libgconfbackend-evoldap.so  \
/usr/lib/libgconf2-4/2/libgconfbackend-oldxml.so \
/usr/lib/libgconf2-4/2/libgconfbackend-xml.so


```The program has successfully built but had problems with start. 
I’ve got this message: 



```
/home/xray/testLibs-build-desktop/testLibs: error while loading shared libraries: libgconfbackend-evoldap.so: cannot open shared object file: No such file or directory
```So, I’ve decided to set a variable LD_LIBRARY_PATH=/usr/lib/libgconf2-4/2/
After that, I built the program again and then tried to start. I’ve got this:

```
Starting /home/xray/testLibs-build-desktop/testLibs...
*** glibc detected *** /home/xray/testLibs-build-desktop/testLibs: malloc(): memory corruption: 0x09ab7900 ***
======= Backtrace: =========
/lib/libc.so.6(+0x6c501)[0x903501]
/lib/libc.so.6(+0x6f2fc)[0x9062fc]
...
...
b76fe000-b7705000 r--s 00000000 08:07 6393       /usr/lib/gconv/gconv-modules.cache
b7705000-b7706000 r--p 002a1000 08:07 7283       /usr/lib/locale/locale-archive
b7706000-b7708000 rw-p 00000000 00:00 0 
bf7fc000-bf81d000 rw-p 00000000 00:00 0          [stack]
The program has unexpectedly finished.
/home/xray/testLibs-build-desktop/testLibs exited with code 0


```When I’m trying to start program in debug mode and go step by step, I get the exception at this line of code: g_type_init(); // initialization of gconf api
This is the first call of function located in *.so object. It seems to me that body of function located in *.so was not loaded.

Before using QTCreator I compiled console application with this static library in NetBeans IDE. Program has started and implemented successfully. :)
I will appreciate all useful advices. 
Thanks in advance.

---

