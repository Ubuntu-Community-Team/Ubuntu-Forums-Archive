---
title: "iptables owner match not working in 8.10"
date: 2009-02-13
forum: General Help
---

### Post by Dirkomatic on 2009-02-13
I receive:

```
iptables: No chain/target/match by that name
```

whenever I try to use
```
iptables -A OUTPUT -p tcp --dport 8081 -m owner --uid-owner proxy -j ACCEPT
```

or any other valid iptables statement using an owner / --uid-owner match.

This is very frustrating...  I see a few other posts from people with the same issue, but no real resolution.  Is this an issue with the kernel or with iptables?  How can I resolve it?

Thanks.

---

### Post by Dirkomatic on 2009-02-13
This may or may not help, but I recently upgraded from 7.04 to 7.10 to 8.04 to 8.10.

---

