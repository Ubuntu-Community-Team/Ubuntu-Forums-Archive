---
title: "&quot;make&quot; for STunnel dosent work?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by hc2995 on 2006-09-08
ok i installed openSSL and now im trying to get Stunnel to work BUT when i type make (after ./configure) i get this: 

```

Making all in src
make[1]: Entering directory `/home/howard/Desktop/stunnel/src'
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2 -Wall -Wshadow -Wcast-align -Wpointer-arith -I/usr/local/ssl/include   -o libstunnel.la -rpath /usr/local/lib -avoid-version env.lo  -lz -ldl -lutil  -lpthread -L/usr/local/ssl/lib -lssl -lcrypto -lwrap
gcc -shared  .libs/env.o  -lz -ldl -lutil -lpthread -L/usr/local/ssl/lib -lssl -lcrypto -lwrap  -Wl,-soname -Wl,libstunnel.so -o .libs/libstunnel.so
/usr/bin/ld: cannot find -lwrap
collect2: ld returned 1 exit status
make[1]: *** [libstunnel.la] Error 1
make[1]: Leaving directory `/home/howard/Desktop/stunnel/src'
make: *** [all-recursive] Error 1

```

is there a way to get it from the repositorys? (sudo apt-get?) if so whats the sudo apt-get?

---

### Post by hc2995 on 2006-09-08
any help?

---

### Post by hc2995 on 2006-09-08
bumpy bump

---

### Post by deadite66 on 2006-10-06
just had the same problem

install libwrap devel

---

