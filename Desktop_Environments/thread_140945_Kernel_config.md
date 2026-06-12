---
title: "Kernel config?"
date: 2006-03-07
forum: Desktop Environments
---

### Post by davalex on 2006-03-07
Where can i find the kernelconfig for my kernel? (2.6.15-15-386). Need this to compile the drivers for my wireless networkcard. 

Thanks.

---

### Post by az on 2006-03-07
[QUOTE=davalex]Where can i find the kernelconfig for my kernel? (2.6.15-15-386). Need this to compile the drivers for my wireless networkcard. 

Thanks.[/QUOTE]
The config can be found in /boot.

However, you do not need to recompile your kernel.  Just install the linux-headers-2.5.15-386 package and use that as your kernel source - that's what the linux-headers are for.  It even creates a symlink in /lib/modules/`uname -r`/build so that everything works automagically.

Don't even install the linux kernel source.  Just use the kernel you are running.

---

### Post by davalex on 2006-03-07
I know about the headers, but Im only interested in the config, so thank you very mutch azz ;)

---

