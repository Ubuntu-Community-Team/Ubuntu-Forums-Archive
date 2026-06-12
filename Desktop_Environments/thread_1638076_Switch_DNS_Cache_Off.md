---
title: "Switch DNS Cache Off"
date: 2010-12-05
forum: Desktop Environments
---

### Post by TheMegaIdiot on 2010-12-05
Hello,

I believe Ubuntu 10.10 has a DNS cache, how can I disable this?

Thanks,
Jack.

---

### Post by Brandon Williams on 2010-12-06
I don't see any evidence of a local DNS cache on my 10.10 machine. That said, you might still have one running. The three that I'm aware of are: nscd, dnsmasq, and djbdns. They are all in the universe repo, so I doubt they're installed by default in Ubuntu, Kubuntu, or Xubuntu, but I could be wrong.

Anyway, if you do have one of them running, the method for flushing the cache should be the same whichever one it is ... just restart the service. For nscd and dnsmasq, one of these should do the trick:```
sudo /etc/init.d/nscd restart
sudo /etc/init.d/dnsmasq restart
```I'm not sure about djbdns, though.

---

