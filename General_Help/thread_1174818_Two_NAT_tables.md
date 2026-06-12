---
title: "Two NAT tables"
date: 2009-05-31
forum: General Help
---

### Post by Romala on 2009-05-31
Dear friends,

Ubuntu server,
eth1 - WAN, eth0 - LAN,
PPPoE server 192.168.3.0/24,
PPTP server 192.168.4.0/24.

Is it a right code for two NAT tables on an interface eth0:
```
iptables -A INPUT -p gre -j ACCEPT
iptables -A INPUT -m -p tcp --dport 1723 -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -s 192.168.3.0/24 -j MASQUERADE 
iptables -A INPUT -p tcp -j ACCEPT 
iptables -t nat -A POSTROUTING -o eth0 -s 192.168.4.0/24 -j MASQUERADE

```
?
I've found a good example 
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html#INCLUDERCFIREWALL]("http://iptables-tutorial.frozentux.net/iptables-tutorial.html#INCLUDERCFIREWALL")
The problem is to make a table for PPTP and a table for PPPoE server independent.
Thank you for your advices! :p

---

### Post by Romala on 2009-06-01
I've solved by the commands:
```

iptables -A INPUT -p gre -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --dport 1723 -j ACCEPT 
iptables -t nat -A POSTROUTING -s 192.168.4.0/24 -j MASQUERADE
iptables -N pppoe
iptables -A pppoe -p tcp -m tcp --dport 80 -j ACCEPT 
iptables -A pppoe -p tcp -m tcp --dport 22 -j ACCEPT 
iptables -t nat -A POSTROUTING -s 192.168.3.0/24 -j MASQUERADE 

```

The problem is still opened: the chain "INPUT" should be worked only for PPTP-server, the chain "pppoe" - for PPPoE. --- How it can be done?

Thank you in advance!

---

