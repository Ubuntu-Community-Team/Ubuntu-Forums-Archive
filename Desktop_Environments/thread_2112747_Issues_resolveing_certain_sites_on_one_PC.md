---
title: "Issues resolveing certain sites on one PC"
date: 2013-02-05
forum: Desktop Environments
---

### Post by monkeypigs on 2013-02-05
I'm running Ubuntu 12.10 on two different machines.  One of them can access any sites apart from those on my new hosting provider.

I've tried installing and restarting nscd, checked that /etc/resolv.conf seems OK, there is no customisation to /etc/hosts

Both computers use the same DNS servers (although I have tried changing the DNS on the machine having problems to use OpenDNS, which as I though had no effect at all.)

Apart from the fact that I've moved hosting providers recently, they have also moved me  on to a different server (I was on server85, I'm now on server69)

server85 seems to have been cached somewhere, (My cpanel login redirects me here, when it should start s69)

However, a ping of my domain name points correctly to 69

I've tried running  

```
find / -xdev -type f -print0 | xargs -0 grep -H "s85."
```

but nothing is listed. 

Scratching my head as to why only one machine is affected, and only on my new hosts and yet it can be pinged ok (Also, a windows VM with a bridged NIC adaptor is all working fine on the Ubuntu box having trouble)

---

