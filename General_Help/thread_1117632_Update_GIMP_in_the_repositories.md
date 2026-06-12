---
title: "Update GIMP in the repositories"
date: 2009-04-06
forum: General Help
---

### Post by brad82 on 2009-04-06
Would it be possible for someone to update GIMP in the ubuntu repositories, the version in the repos is 2.6.1 I believe, but I would like to use 2.6.6

I have tried compiling my own 2.6.6, but failed and wont start..


Ta

---

### Post by kpkeerthi on 2009-04-06
[http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

---

### Post by brad82 on 2009-04-06
I installed it, but GIMP still doesnt load, it just pops up in the taskbar, and then disappears. Any ideas?

---

### Post by drs305 on 2009-04-06
> **brad82 said:**
> I installed it, but GIMP still doesnt load, it just pops up in the taskbar, and then disappears. Any ideas?

Try running gimp from the terminal and see what error messages you get, if any:
```

gimp --verbose 

```

---

### Post by 3rdalbum on 2009-04-06
Try following the instructions to remove the compiled version of Gimp, and then reinstall the Getdeb.net version of Gimp.

Or try specifying /usr/bin/gimp rather than just "gimp" - as just "gimp" might be resolving to /usr/local/bin/gimp which is the locally-compiled one.

---

### Post by brad82 on 2009-04-06
Heres what I get when I start it in terminal

```
brad@Brads-Laptop:~$ /usr/bin/gimp
babl-db.c:98 babl_db_insert()     
        Eeeeek                    
(no debugging symbols found)      
[Thread debugging using libthread_db enabled]
[New Thread 0xb728b910 (LWP 6696)]           
0xb8042430 in __kernel_vsyscall ()           
#0  0xb8042430 in __kernel_vsyscall ()       
#1  0xb75c1733 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb755e78b in ?? () from /lib/tls/i686/cmov/libc.so.6     
#3  0xb769150d in system () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb77c292e in babl_backtrack () at babl-internal.c:68
#5  0xb77c2967 in babl_die () at babl-internal.c:74
#6  0xb77bb5cf in babl_db_insert (db=0x878df90, item=0x0) at babl-db.c:98
#7  0xb77bd9e8 in babl_extension_init () at babl-extension.c:197
#8  0xb77baecd in babl_init () at babl.c:40
---Type <return> to continue, or q <return> to quit---
#9  0xb78492f2 in gegl_post_parse_hook (context=0x877dec8, group=0x87821c0, data=0x0, error=0xbff423d4) at gegl-init.c:483
#10 0xb76e4803 in g_option_context_parse () from /usr/lib/libglib-2.0.so.0
#11 0x080a674f in main ()

```

Something to do with babl?

---

