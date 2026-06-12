---
title: "ssh hangs connecting to Unix machines"
date: 2009-04-20
forum: General Help
---

### Post by superdave8000 on 2009-04-20
I've traced this down, I think, to kernel 2.6.18. On any machines with that kernel, I cannot ssh into a Unix (BSD) machine; the process hangs at the debug message "SSH2_MSG_KEXINIT sent". 

This seems to be a major problem - does anybody have any ideas how to fix? Seems the ssh server/client versions don't matter - only the kernel version.

TIA!

---

### Post by superdave8000 on 2009-04-20
Please disregard - I found the problem within OpenBSD3.9's PF state tables.

---

