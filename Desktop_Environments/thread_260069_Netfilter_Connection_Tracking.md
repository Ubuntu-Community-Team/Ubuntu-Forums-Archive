---
title: "Netfilter Connection Tracking"
date: 2006-09-18
forum: Desktop Environments
---

### Post by AxelF on 2006-09-18
Hello,

I am using Shorewall on Dapper and I was wondering how to adjust the connection tracking limit.  I know when the ip_conntrack module is loaded it automatically chooses a connection limit but I would like to set this higher.  I tried adding an entry in sysctl.conf for net.ipv4.netfilter.ip_conntrack_max but the this value doesn't exist until ip_conntrack gets loaded by Shorewall.  When it does I  see the the following in my syslog:

firewall kernel: [42949385.870000] ip_conntrack version 2.4 (8190 buckets, 65520 max) - 232 bytes per conntrack

Once the module is loaded I can use sysctl -w to change the value of net.ipv4.netfilter.ip_conntrack_max but I am not sure it is really taking effect.  It seems to me I need to specify this before the ip_conntrack module gets loaded, but I don't know where to do it.

Any help is appreciated.

TIA!

---

