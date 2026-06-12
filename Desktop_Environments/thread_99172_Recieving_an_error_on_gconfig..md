---
title: "Recieving an error on gconfig."
date: 2005-12-05
forum: Desktop Environments
---

### Post by Septicaemia on 2005-12-05
I'm compiling a new Vanilla kernel for myself.. and i'm getting:

  HOSTCC  scripts/basic/fixdep
In file included from /usr/include/sys/socket.h:35,
                 from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:304:24: error: asm/socket.h: No such file or directory
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

When I run "make gconfig", any ideas?


Thanks,
Brendan.

---

### Post by John Dooley on 2006-01-12
I tried gconfig and it could not find several packages: gtk+-2.0, glade-2.0, + in the repository. It looks like it is not supported. 

I noticed that someone was using xconfig. 

I ended up using menuconfig which required installing libncurses5-dev which I found in the repository. 

menuconfig is primitive. xconfig is fancy. It looks like the ubuntu team decided that support for gconfig was redundant and just another fancy GUI.

---

### Post by John Dooley on 2006-01-13
I gave xconfig a try. make xconfig resulted in "can't find" messages. After running the synaptic package manager xconfig came up.

This is much easier on the eyes than menu config.

I guess gconfig is the odd guy out. Should this be entered as a bug?

---

