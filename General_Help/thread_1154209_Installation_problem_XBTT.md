---
title: "Installation problem XBTT"
date: 2009-05-09
forum: General Help
---

### Post by olol on 2009-05-09
Hi, I'm trying to set this tracker up, And I thought I might try the non php announce system. So I figure XBTT would be the best, just that it wont let me install it.. :/
Have googled like a maniac with some luck, but now I just ran out of luck..

So I'll try you guys out, any idéa what might be wrong? 

Last lines of code after "make"

```
In file included from xcc_z.cpp:6:
stream_int.h: In function ‘T write_float(T, float)’:
stream_int.h:26: error: there are no arguments to ‘memcpy’ that depend on a template parameter, so a declaration of ‘memcpy’ must be available
stream_int.h:26: error: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
make[4]: *** [xcc_z.lo] Error 1
make[4]: Leaving directory `/var/www/tracker/xbtt/build/xbtt/src/misc'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/var/www/tracker/xbtt/build/xbtt/src/misc'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/www/tracker/xbtt/build/xbtt/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/www/tracker/xbtt/build/xbtt'
make: *** [all] Error 2

```

---

