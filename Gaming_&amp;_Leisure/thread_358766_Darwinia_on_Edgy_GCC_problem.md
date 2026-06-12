---
title: "Darwinia on Edgy GCC problem"
date: 2007-02-11
forum: Gaming &amp; Leisure
---

### Post by blackcougar on 2007-02-11
Hi

I have installed Darwinia on my computer but when i run it i get
```
jozzy@L13n4D:~$ ./Programs/darwinia/darwinia 
./Programs/darwinia
./Programs/darwinia/lib/darwinia.bin.x86: ./Programs/darwinia/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
jozzy@L13n4D:~$ 

```

I have installed all packages from apt-get which have gcc or libstdc++ in them but it still is the same.

I can't find any packages for GCC 4.2 either for apt-get

Anybody have any ideas, pointers?

Josh

---

### Post by aidanr on 2007-02-11
delete or rename/backup ./Programs/darwinia/lib/libgcc_s.so.1

---

### Post by blackcougar on 2007-02-11
Your fix worked
Thanks a ton,

This has to be the fastest forum i've been on!!

---

