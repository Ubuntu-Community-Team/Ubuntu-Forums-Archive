---
title: "How Can I Tell apt Not To Use ipv6?"
date: 2006-03-17
forum: Desktop Environments
---

### Post by bakert on 2006-03-17
apt can't resolve any domain names because it tries to use ipv6 which doesn't work with my router.

Does anyone know how I can tell/force apt to use ipv4?

Thanks,

Tom

---

### Post by bakert on 2006-04-02
I think I was mixing up two problems here.  I did have a problem with ipv6 not working with my router.  But the reason apt could not resolve domain names was to do with the nameserver being set by DHCP to be the router's address.

I found a fairly workable answer here (elithrar's post):

[http://ubuntuforums.org/showthread.php?t=141728&page=2](http://ubuntuforums.org/showthread.php?t=141728&page=2)

---

