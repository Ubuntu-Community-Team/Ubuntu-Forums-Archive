---
title: "How to fix &quot;version `GLIBC_2.7' not found&quot; error"
date: 2009-04-09
forum: General Help
---

### Post by megatro on 2009-04-09
Hello,

I am trying to use chroot on an Ubuntu 8.10 version system.

I have copied all the lib files in the path of the command that I want to be the new root (jail).

Here is the command sequence:

p:~$ sudo chroot ~/<cmd> /bin/ash
[sudo] password for megator: 
/bin/ash: /lib/tls/libc.so.6: version `GLIBC_2.7' not found (required by /bin/ash)
/bin/ash: /lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by /bin/ash)
/bin/ash: /lib/tls/libc.so.6: version `GLIBC_2.8' not found (required by /bin/ash)

How can I fix this error?

TIA for your help

---

