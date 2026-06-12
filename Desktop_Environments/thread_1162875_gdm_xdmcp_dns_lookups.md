---
title: "gdm xdmcp dns lookups"
date: 2009-05-18
forum: Desktop Environments
---

### Post by mcfirstlast on 2009-05-18
hi
 
When making a remote X connection using XDMCP after the first udp/177 packet has reached the X server (hostname 'workstation', IP 192.168.240.106) the gdm process on the X server then tries to do a IPv6 DNS lookup of itself ('workstation.internet.local') to the external nameserver specified in /etc/resolv.conf. The response to this lookup is obviously 'ServFail', as this box is behind NAT and not externally facing at all.
I have made no modifications to /etc/gdm/gdm.conf, simply just enabled remote X connections using the 'Login Window' menu item thingy.
 
Here is some info to make things clearer:
 
uname -a
```

Linux workstation 2.6.27-14-generic #1 SMP Wed Apr 15 18:59:16 UTC 2009 i686 GNU/Linux

```
 
/etc/hosts
```
 
127.0.0.1       localhost
192.168.240.106 workstation     workstation.internet.local
fe80::223:7dff:fe9f:f9ea        workstation.internet.local

```
 
I have tried blacklisting IPv6 and still no luck. Why would'nt GDM use the static mapping in /etc/hosts? I'm at a loss...
 
Any help gratefully received.

---

