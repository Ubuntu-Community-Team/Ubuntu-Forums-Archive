---
title: "E17 - Evas compile problem"
date: 2009-07-23
forum: Desktop Environments
---

### Post by christopher.adams360 on 2009-07-23
Hi all,

I'm trying to install E17 using easy_e17.sh, and I've done it before, the only issues being dependencies, and once they were satisfied, I just ran the script again.

     
     ```
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../../../.. -I. -I../../../../src/lib -I../../../../src/lib/include -I../../../../src/modules/engines -I../../../../src/modules/engines/software_16 -I/usr/include/freetype2 -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include -D_GNU_SOURCE -MT module_la-evas_x_buffer.lo -MD -MP -MF .deps/module_la-evas_x_buffer.Tpo -c evas_x_buffer.c  -fPIC -DPIC -o .libs/module_la-evas_x_buffer.o
In file included from evas_x_buffer.c:2:
evas_engine.h:7:33: error: X11/extensions/XShm.h: No such file or directory
In file included from evas_engine.c:3:
evas_engine.h:7:33: error: X11/extensions/XShm.h: No such file or directory
In file included from evas_engine.c:3:
evas_engine.h:20: error: expected specifier-qualifier-list before ‘XShmSegmentInfo’
In file included from evas_x_buffer.c:2:
evas_engine.h:20: error: expected specifier-qualifier-list before ‘XShmSegmentInfo’
evas_x_buffer.c: In function ‘evas_software_x11_x_output_buffer_new’:
evas_x_buffer.c:51: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:55: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:55: error: ‘XShmSegmentInfo’ undeclared (first use in this function)
evas_x_buffer.c:55: error: (Each undeclared identifier is reported only once
evas_x_buffer.c:55: error: for each function it appears in.)
evas_x_buffer.c:56: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:59: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:59: warning: assignment makes pointer from integer without a cast
evas_x_buffer.c:62: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:66: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:68: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:69: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:70: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:71: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:79: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:90: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:91: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:96: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:96: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:97: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:110: error: ‘X_Output_Buffer’ has no member named ‘data’
evas_x_buffer.c: In function ‘evas_software_x11_x_output_buffer_free’:
evas_x_buffer.c:134: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:137: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:139: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:140: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:141: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
evas_x_buffer.c:145: error: ‘X_Output_Buffer’ has no member named ‘data’
evas_x_buffer.c: In function ‘evas_software_x11_x_output_buffer_paste’:
evas_x_buffer.c:154: error: ‘X_Output_Buffer’ has no member named ‘shm_info’
make[5]: *** [module_la-evas_x_buffer.lo] Error 1
make[5]: *** Waiting for unfinished jobs....
make[5]: *** [module_la-evas_engine.lo] Error 1
make[5]: Leaving directory `/home/christopher/e17_src/evas/src/modules/engines/software_16_x11'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/christopher/e17_src/evas/src/modules/engines'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/christopher/e17_src/evas/src/modules'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/christopher/e17_src/evas/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/christopher/e17_src/evas'
make: *** [all] Error 2 
```
I'm on Ubuntu 9.04. Sorry for the long post!

Thanks, Chris

---

### Post by szamot83 on 2009-07-25
Hello,

You should install x11proto-xext-dev and libxext-dev packages.

---

### Post by christopher.adams360 on 2009-07-27
Oh I wasn't paying attention. Thanks

---

