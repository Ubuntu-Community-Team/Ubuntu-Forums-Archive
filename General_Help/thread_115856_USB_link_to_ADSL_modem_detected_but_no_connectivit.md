---
title: "USB link to ADSL modem detected but no connectivity"
date: 2006-01-11
forum: General Help
---

### Post by sonytony18 on 2006-01-11
I have connected by laptop (Thinkpad R32) running Breezy to my ISP provided DSL modem (Huawei MT882) via the USB cable. 

The moment I plug in the cable a connection eth1 appears. 

When I configure the connection with DHCP (the modem has DHCP enabled) and activate it I get a IPv6 address on the interface - fe80::20f:a3ff:fe55:15e6/64 and the route table is empty.

When I configure the connection with a static IP of 192.168.1.110 and the modem as the gateway(192.168.1.1), running ifconf shows the IPv4 address as 192.168.1.110 along with the previous IPv6 address
The route table shows that eth1 is the interface to use for 192.168.1.0, and default gateway to be 192.168.1.1 also via eth1.

However I am unable to ping to my modem and cannot connect to the Internet. I cant figure what to do... can someone help ??:???:

---

