---
title: "iptables, bittorrent, not working."
date: 2005-12-27
forum: General Help
---

### Post by eniacpx on 2005-12-27
I am pulling my hair out here, I have read several sites on how to set this up and each one tells me the same thing, which doesn't work on my system.

Here is my setup:

[internet]
 |
 |
[shinon (Ubuntu 5.10 router, 192.168.1.1)]
 |
 |
Switch
 |
 |
[osiris (Ubuntu 5.10 desktop, 192.168.1.100)]

iptables config:
iptables -L:
```

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning
DROP       all  --  127.0.0.0/8          anywhere
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  192.168.1.0/24       anywhere
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4
LOG        all  --  192.168.1.0/24       anywhere            LOG level warning
DROP       all  --  192.168.1.0/24       anywhere
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  anywhere             pcp04204749pcs.brghtn01.mi.comcast.net
ACCEPT     all  --  anywhere             255.255.255.255
LOG        all  --  anywhere             anywhere            LOG level warning
DROP       all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  192.168.1.0/24       anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
LOG        all  --  anywhere             192.168.1.0/24      LOG level warning
DROP       all  --  anywhere             192.168.1.0/24
LOG        all  --  anywhere             anywhere            LOG level warning
DROP       all  --  anywhere             anywhere
ACCEPT     tcp  --  osiris               anywhere            tcp dpts:50000:60000

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  anywhere             192.168.1.0/24
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4
LOG        all  --  anywhere             192.168.1.0/24      LOG level warning
DROP       all  --  anywhere             192.168.1.0/24
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  pcp04204749pcs.brghtn01.mi.comcast.net  anywhere
ACCEPT     all  --  255.255.255.255      anywhere
LOG        all  --  anywhere             anywhere            LOG level warning
DROP       all  --  anywhere             anywhere

```

iptables -t nat -L:
```

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  anywhere             anywhere            tcp dpts:50000:60000 to:192.168.1.100

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  192.168.1.0/24       anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

I am using ports 50000-60000 for bittorrent BTW. 

No tracker can connect to me, nor can I connect to any tracker. What am I doing wrong here? 
Please tell me if you need more info.

---

### Post by njzillest on 2006-01-26
well... you dont really need a firewall.. also check on your router if your outside the NAT firewall... (it should say to isolate your IP adress from the firewall.) That usually is a problem when portforewarding.

---

