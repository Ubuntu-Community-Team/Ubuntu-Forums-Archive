---
title: "Ulimit -n value not setting"
date: 2009-06-03
forum: General Help
---

### Post by sn0rcha on 2009-06-03
Hey guys,

I'm having a hard time getting my ulimit -n value to stay set.

I've altered the /etc/security/limits.conf and added the line;

* hard nofile 32000

also tried with my username

snorcha hard nofile 32000

Everytime I reboot it reverts back to 1024.

I can set it fine in the console using ulimit -n 32000, but it resets on reboot.. Is there something i'm doing wrong? I'm using Jaunty 64.

Cheers,
snorcha

---

