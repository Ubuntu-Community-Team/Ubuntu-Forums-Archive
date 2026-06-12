---
title: "steamdlfilter - Steam Download Filter"
date: 2015-12-18
forum: Gaming &amp; Leisure
---

### Post by matthew124 on 2015-12-18
I have been trying to get this program [https://github.com/instantepiphany/steamdlfilter](https://github.com/instantepiphany/steamdlfilter) to compile but I'm rapidly realising I have no idea what I'm doing. 

I have two questions,

1. Does anyone know of a simpler/easier to set up program that limits steam servers?

2. If not what do these errors mean and how do I fix them?

(When trying to compile steamdlfiltercfg)
```

root@pc:/home/user/Desktop/steamdlfilter-master# gcc -lconfig `pkg-config --cflags gtk+-3.0` -o steamdlfiltercfg steamdlfiltercfg.c `pkg-config --libs gtk+-3.0` -Wall
/tmp/cc6pbD5v.o: In function `toggle_filter':
steamdlfiltercfg.c:(.text+0x94): undefined reference to `config_setting_set_bool'
steamdlfiltercfg.c:(.text+0xc2): undefined reference to `config_setting_set_bool'
steamdlfiltercfg.c:(.text+0xf0): undefined reference to `config_write_file'
/tmp/cc6pbD5v.o: In function `toggle_logging':
steamdlfiltercfg.c:(.text+0x18a): undefined reference to `config_setting_set_bool'
steamdlfiltercfg.c:(.text+0x1b8): undefined reference to `config_setting_set_bool'
steamdlfiltercfg.c:(.text+0x1e6): undefined reference to `config_write_file'
/tmp/cc6pbD5v.o: In function `save_server':
steamdlfiltercfg.c:(.text+0x258): undefined reference to `config_lookup'
steamdlfiltercfg.c:(.text+0x26f): undefined reference to `config_setting_set_string'
steamdlfiltercfg.c:(.text+0x282): undefined reference to `config_write_file'
/tmp/cc6pbD5v.o: In function `main':
steamdlfiltercfg.c:(.text+0x3a4): undefined reference to `config_init'
steamdlfiltercfg.c:(.text+0x3bd): undefined reference to `config_read_file'
steamdlfiltercfg.c:(.text+0x40f): undefined reference to `config_destroy'
steamdlfiltercfg.c:(.text+0x42d): undefined reference to `config_lookup'
steamdlfiltercfg.c:(.text+0x443): undefined reference to `config_setting_get_bool'
steamdlfiltercfg.c:(.text+0x472): undefined reference to `config_lookup'
steamdlfiltercfg.c:(.text+0x488): undefined reference to `config_setting_get_bool'
steamdlfiltercfg.c:(.text+0x4be): undefined reference to `config_lookup_string'
steamdlfiltercfg.c:(.text+0x6b0): undefined reference to `config_setting_get_bool'
steamdlfiltercfg.c:(.text+0x7f7): undefined reference to `config_setting_get_bool'
steamdlfiltercfg.c:(.text+0x99a): undefined reference to `config_write_file'
steamdlfiltercfg.c:(.text+0x9a9): undefined reference to `config_destroy'
collect2: error: ld returned 1 exit status
root@pc:/home/user/Desktop/steamdlfilter-master# 

```

(When I try to compile steamdlfilter)

```

root@pc:/home/user/Desktop/steamdlfilter-master# gcc -Wall -m32 -shared -fPIC -L/usr/local/lib -lconfig -ldl steamdlfilter.c -o steamdlfilter.so -D_GNU_SOURCE
steamdlfilter.c:1:24: fatal error: sys/socket.h: No such file or directory
 #include <sys/socket.h>
                        ^
compilation terminated.
root@pc:/home/user/Desktop/steamdlfilter-master# 

```

Thanks in advance for any help you can offer.

---

### Post by deepakdeshp on 2015-12-18
If you mean steam then here is the procedure
[http://itsfoss.com/install-steam-ubuntu-linux/](http://itsfoss.com/install-steam-ubuntu-linux/)

---

