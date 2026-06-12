---
title: "dmesg output"
date: 2009-01-27
forum: General Help
---

### Post by eppo on 2009-01-27
i'm getting these messages in dmesg, what exactly do they mean?
[129647.744291] type=1503 audit(1233039887.194:43): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=112 name="/proc/5339/net/if_inet6" pid=5341 profile="/usr/sbin/named"
and how can i get them to stop?
thanks

---

### Post by bgerlich on 2009-01-27
Probably it's because of apparmor or running bind9 in chroot. Try to disable apparmor and see if it still occurs.

---

