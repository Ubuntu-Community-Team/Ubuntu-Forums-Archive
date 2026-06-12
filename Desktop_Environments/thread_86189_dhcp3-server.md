---
title: "dhcp3-server"
date: 2005-11-04
forum: Desktop Environments
---

### Post by UbU[nl] on 2005-11-04
Hi

I run a dhcp server on Ubuntu 5.10, everything works fine.

But when a aks with my computers on the network a ip.
The server starts with giving them from .20 to .10

How it coms it's working the 'correct' way .10 .11 .12 ...

Here you can see the config file:
```

ddns-update-style none;

subnet 192.168.5.0 netmask 255.255.255.0 {
  range 192.168.5.10 192.168.5.20;
  option domain-name-servers 192.168.5.99;
  option domain-name "nice_lan.lan";
  option routers 192.168.5.99;
  default-lease-time 1234;
}

```

---

