---
title: "dhcp server"
date: 2012-02-07
forum: Egypt Team
---

### Post by mustafa ibrahim on 2012-02-07
&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605; &#1608;&#1585;&#1581;&#1605;&#1577; &#1575;&#1604;&#1604;&#1607; &#1608;&#1576;&#1585;&#1603;&#1575;&#1578;&#1607;
&#1575;&#1585;&#1580;&#1608; &#1575;&#1604;&#1575;&#1601;&#1575;&#1583;&#1607;


dhcp server
root@mustafa-sr1:/home/mustafa-sr1# vim /etc/dhcp3/dhcpd.conf
root@mustafa-sr1:/home/mustafa-sr1# /etc/init.d/dhcp3-server restart
* Stopping DHCP server dhcpd3 [fail] 
* Starting DHCP server dhcpd3 * check syslog for diagnostics.

default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 10.0.0.255;
option routers 10.0.0.138;
subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.10 10.0.0.200;
host server1 {
hardware ethernet 00:15:00:24:5c:b0;
fixed-address 10.0.0.11;
}
}

on syslog

Feb 5 22:22:15 mustafa-sr1 dhcpd: Wrote 0 deleted host decls to leases file.
Feb 5 22:22:15 mustafa-sr1 dhcpd: Wrote 0 new dynamic host decls to leases file.
Feb 5 22:22:15 mustafa-sr1 dhcpd: Wrote 0 leases to leases file.
Feb 5 22:22:15 mustafa-sr1 dhcpd: 
Feb 5 22:22:15 mustafa-sr1 dhcpd: No subnet declaration for eth0:138 (0.0.0.0).
Feb 5 22:22:15 mustafa-sr1 dhcpd: ** Ignoring requests on eth0:138. If this is not what
Feb 5 22:22:15 mustafa-sr1 dhcpd: you want, please write a subnet declaration
Feb 5 22:22:15 mustafa-sr1 dhcpd: in your dhcpd.conf file for the network segment
Feb 5 22:22:15 mustafa-sr1 dhcpd: to which interface eth0:138 is attached. **
Feb 5 22:22:15 mustafa-sr1 dhcpd: 
Feb 5 22:22:15 mustafa-sr1 dhcpd: 
Feb 5 22:22:15 mustafa-sr1 dhcpd: Not configured to listen on any interfaces!
[http://255.255.255.0/](http://255.255.255.0/)
&#8206;255.255.255.0
Like · · Unfollow Post · Share · 28 minutes ago
Mustafa Ibrahim on restart root@mustafa-sr1:/home/mustafa-sr1# /etc/init.d/dhcp3-server restart
* Stopping DHCP server dhcpd3 [fail] 
* Starting DHCP server dhcpd3 * check syslog for diagnostics.

---

### Post by saphil on 2012-02-14
Your post is missing it's question. You get better responses if you are more descriptive in your requests for help. :-)

Suggestions:

subnet mask seems wrong
That is an "A" class network, are you subnetting it to "C" class networks? If not, you want a subnet mask of 255.0.0.0 

Your host server IP should not be in your dhcp range - suggest using 10.0.0.2 for host server address. Host dhcp server address should be a static address.

Router should be a static address.  Suggest 10.0.0.1 Set on router proper and note here on the dhcp server setup.  This is your network gateway.

Cheers,
Wolf

---

