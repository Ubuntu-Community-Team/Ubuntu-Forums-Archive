---
title: "mdk3 compiling error"
date: 2009-01-02
forum: General Help
---

### Post by heavyhanded on 2009-01-02
I'm having trouble compiling mdk3 on my xubuntu 8.04 system.  

I've done some searching and came across posts recommending installing gcc-4.2 and referencing it in /osdep/common.mak, which I've done.

However, I am still getting the following make error:

```
make -C osdep
make[1]: Entering directory `/home/cb/mdk3/mdk3-v5/osdep'
Building for Linux
make[2]: Entering directory `/home/cb/mdk3/mdk3-v5/osdep'
gcc-4.2 -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v5  -fPIC -I..    -c -o osdep.o osdep.c
osdep.c:21:20: error: stdlib.h: No such file or directory
osdep.c:22:20: error: assert.h: No such file or directory
osdep.c:23:20: error: string.h: No such file or directory
In file included from osdep.c:25:
osdep.h:11:24: error: netinet/in.h: No such file or directory
osdep.h:12:20: error: stdint.h: No such file or directory
In file included from osdep.c:25:
osdep.h:26: error: expected specifier-qualifier-list before ‘uint64_t’
cc1: warnings being treated as errors
osdep.h:106: warning: ‘struct in_addr’ declared inside parameter list
osdep.h:106: warning: its scope is only this definition or declaration, which is probably not what you want
osdep.h:127: warning: ‘struct in_addr’ declared inside parameter list
In file included from osdep.c:26:
network.h:11:22: error: inttypes.h: No such file or directory
network.h:12:23: error: sys/types.h: No such file or directory
In file included from osdep.c:26:
network.h:30: error: expected specifier-qualifier-list before ‘uint8_t’
osdep.c: In function ‘wi_read’:
osdep.c:30: warning: implicit declaration of function ‘assert’
osdep.c: In function ‘wi_alloc’:
osdep.c:94: warning: implicit declaration of function ‘malloc’
osdep.c:94: warning: incompatible implicit declaration of built-in function ‘malloc’
osdep.c:96: error: ‘NULL’ undeclared (first use in this function)
osdep.c:96: error: (Each undeclared identifier is reported only once
osdep.c:96: error: for each function it appears in.)
osdep.c:97: warning: implicit declaration of function ‘memset’
osdep.c:97: warning: incompatible implicit declaration of built-in function ‘memset’
osdep.c:101: warning: implicit declaration of function ‘free’
osdep.c: In function ‘wi_open’:
osdep.c:148: error: ‘NULL’ undeclared (first use in this function)
osdep.c:150: warning: implicit declaration of function ‘strncpy’
osdep.c:150: warning: incompatible implicit declaration of built-in function ‘strncpy’
osdep.c: At top level:
osdep.c:199: warning: ‘struct in_addr’ declared inside parameter list
osdep.c:200: error: conflicting types for ‘ti_set_ip’
osdep.h:127: error: previous declaration of ‘ti_set_ip’ was here
osdep.c: In function ‘ti_set_ip’:
osdep.c:202: warning: passing argument 2 of ‘ti->ti_set_ip’ from incompatible pointer type
osdep.c: In function ‘ti_alloc’:
osdep.c:211: warning: incompatible implicit declaration of built-in function ‘malloc’
osdep.c:213: error: ‘NULL’ undeclared (first use in this function)
osdep.c:214: warning: incompatible implicit declaration of built-in function ‘memset’
make[2]: *** [osdep.o] Error 1
make[2]: Leaving directory `/home/cb/mdk3/mdk3-v5/osdep'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/cb/mdk3/mdk3-v5/osdep'
make: *** [osd] Error 2
```

Any sugestions? I havent compiled a program for ages, since ubuntu came along with it's damn easy package management system.:D

---

### Post by dexter on 2009-01-02
Seems like you don't have any of the standard header files. Is the build-essentials package installed?

---

