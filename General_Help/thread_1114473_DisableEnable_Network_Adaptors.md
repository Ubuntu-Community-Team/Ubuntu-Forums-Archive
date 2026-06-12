---
title: "Disable/Enable Network Adaptors"
date: 2009-04-02
forum: General Help
---

### Post by Bortiquai on 2009-04-02
Using Ubuntu 8.10 - 

I have a computer with 2 NICs.  They are on two different networks.  Sometimes, for testing, etc... I need to disable one, enable the other, enable both, disable both.... you get it.

How can I do this?  Seems like they are both always enabled and I can't figure out how to shut them off individually.

Thanks

---

### Post by dcstar on 2009-04-02
> **Bortiquai said:**
> Using Ubuntu 8.10 - 

I have a computer with 2 NICs.  They are on two different networks.  Sometimes, for testing, etc... I need to disable one, enable the other, enable both, disable both.... you get it.

How can I do this?  Seems like they are both always enabled and I can't figure out how to shut them off individually.

Thanks

```
man ifdown
```

---

### Post by HermanAB on 2009-04-02
$ sudo killall dhclient
$ sudo ifconfig eth1 down
$ sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up
$ sudo route add default gw 192.168.1.254
$ ping [www.yahoo.com](www.yahoo.com)

'Hope that helps!

---

