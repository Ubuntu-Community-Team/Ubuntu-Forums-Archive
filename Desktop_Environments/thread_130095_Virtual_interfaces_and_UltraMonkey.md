---
title: "Virtual interfaces and UltraMonkey"
date: 2006-02-15
forum: Desktop Environments
---

### Post by xraycharlie on 2006-02-15
Hello,

I've been playing around will UltraMonkey and have finally gotten it all to work.... With one exception.

I set up the virtual interface of the real-server:

auto lo:0
iface lo:0 inet static
  address 192.168.6.240
  netmask 255.255.255.255
  pre-up sysctl -p > /dev/null

Then bring it up with a: /sbin/ifup lo:0

Everything works great. Until I restart the read-server.

lo:0 does not automatically come up and I have to manually do another 'ifup lo:0'.

How to I get lo:0 to automagically come up on a restart?

Regards

---

