---
title: "synaptic post-install crashes"
date: 2006-01-28
forum: Desktop Environments
---

### Post by PascalGR on 2006-01-28
Hi,

After an update of my linux box using synaptic, post-install of packages crashes every time. I've researched the problem and found that the script:

[I]/var/lib/dpkg/info/dhelp.postinst
[/I]
outputs a segmentation fault at line 45, when it executes:

*/usr/sbin/dhelp_parse -r*


In a detailed investigation with strace, I've noticed that the the last system calls it called were:

```
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7cd1000
lstat64("/usr", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/share", {st_mode=S_IFDIR|0755, st_size=8192, ...}) = 0
lstat64("/usr/share/doc", {st_mode=S_IFDIR|0755, st_size=49152, ...}) = 0
lstat64("/usr/share/doc/HTML", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
**getcwd("/usr/share/doc/HTML/debian", 4096) = 27**
```

followed by:
```
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
```

Any help on how to fix post-install please?

---

