---
title: "Adresses resolving to 1.0.0.0"
date: 2006-06-20
forum: Desktop Environments
---

### Post by adwait on 2006-06-20
I just installled Dapper on a new computer, and due to some wierd reason, some addresses seem to resolve to 1.0.0.0? Sometimes they resolve correctly sometimes they don't. I have tried turning off pv6 off, but it still seems to be on. What do I do??

---

### Post by g00n on 2006-06-22
I've had a post open on this for 2 weeks, with no response... only happens on my ISP router, not my dlink router.

it is an IPV6 issue, but it's more with your router dns server than with ubuntu.

The comp is making ipv6 dns requests 1st, and instead of the dns server ignoring or rejecting them, they're responding with 1.0.0.0 .

to work around it, make sure your /etc/resolv.conf doesn't have your router in there as a nameserver.

IF you can stop ubuntu from making the ipv6 requests that woudl also solve it.

---

### Post by greg.harvey on 2008-02-04
I did this, and then did this to confirm IPv6 is not enabled:

```
ip a | grep inet6
```

However I still have the same issue. So it can't be caused by IPv6?

---

