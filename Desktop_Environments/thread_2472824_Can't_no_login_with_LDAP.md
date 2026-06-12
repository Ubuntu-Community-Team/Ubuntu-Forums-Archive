---
title: "Can't no login with LDAP"
date: 2022-03-14
forum: Desktop Environments
---

### Post by rezagpm on 2022-03-14
Hi, forgive me for my bad english.

I'm trying to connect to my laptop using my enterprise credentials (kerberos, sssd). If i try to connect using ssh, it works. But when i try with GDM3,
the display returns to the login form autmatically.

In the log I found that:
```
systemd-logind: failed to get session: PID 2112 does not belong to any known session
```

I found over the net some solutions without any success:
- install nscd
- Modify ystemd-logind: failed to get session: PID 2112 does not belong to any known session
```
RestrictAddressFamilies=AF_UNIX AF_NETLINK AF_INET AF_INET6
IPAddressAllow=any

```

I have exactly the same problem with GDM or startx.

A local posix account works well.

Any idea please ??

---

