---
title: "No hosts file - just hosts.allow and .deny"
date: 2011-01-26
forum: Desktop Environments
---

### Post by caradeporra on 2011-01-26
Ok,

  Probably an easy (which means stoopid) question...I am trying to reroute a website using my hosts file so that it matches my servers certificate file for testing without effect dns and the live site.

  When I went to edit my /etc/hosts file it is non-existent.  I have, I am assuming in it's place, hosts.allow and hosts.deny.  Can anyone explain why I do not have a hosts file?

Thanks,
Carade

---

### Post by Krytarik on 2011-01-26
I don't know why you don't have the "hosts" file, searched the web for it: no results, only "create one".

Well then just create one ;-), my "hosts" file starts with the following entries, those are the default entries, besides the "krytarik" of course:
```
127.0.0.1    localhost
127.0.1.1    krytarik-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

