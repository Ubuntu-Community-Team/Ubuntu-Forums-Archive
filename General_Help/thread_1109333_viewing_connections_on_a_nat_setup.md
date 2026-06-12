---
title: "viewing connections on a nat setup"
date: 2009-03-28
forum: General Help
---

### Post by sinclair86 on 2009-03-28
i have a computer nat'ed thru my ubuntu how can i just see the current connections kinda like netstat but for nat?

---

### Post by lovinglinux on 2009-03-28
I'm not sure because I don't use this kind of setup, but maybe iptraf would tell you that.

```
sudo apt-get install iptraf
```

---

### Post by sinclair86 on 2009-03-28
forund easier way

```
sudo cat /proc/net/ip_conntrack | grep "ESTABLISHED src=[nat ip]"
```

---

