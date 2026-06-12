---
title: "Atlantik not compiling"
date: 2007-01-06
forum: Gaming &amp; Leisure
---

### Post by maddog39 on 2007-01-06
Hello all,

I made a slightly modified version of Atlantik for personal usage but it wont compile. I keep getting this error:
```

Making all in libatlantic
make[3]: Entering directory `/home/maddog39/Desktop/atlantik-0.7.1/atlantik/libatlantic'
source='atlantic_core.cpp' object='atlantic_core.lo' libtool=yes \
        depfile='.deps/atlantic_core.Plo' tmpdepfile='.deps/atlantic_core.TPlo' \
        depmode=gcc3 /bin/bash ../../admin/depcomp \
        /bin/bash ../../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.    -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -c -o atlantic_core.lo `test -f atlantic_core.cpp || echo './'`atlantic_core.cpp
trade.h: In member function 'Type* Trade::select(Player*, Player*)':
trade.h:124: error: 'class Player' has no member named 'from'
trade.h:125: error: 'class Player' has no member named 'to'
make[3]: *** [atlantic_core.lo] Error 1
make[3]: Leaving directory `/home/maddog39/Desktop/atlantik-0.7.1/atlantik/libatlantic'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/maddog39/Desktop/atlantik-0.7.1/atlantik'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/maddog39/Desktop/atlantik-0.7.1'
make: *** [all] Error 2

```
But I've only modified one file, and that's not it. Any ideas?

Thanks!
-maddog39

---

