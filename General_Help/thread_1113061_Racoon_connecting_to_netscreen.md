---
title: "Racoon connecting to netscreen"
date: 2009-04-01
forum: General Help
---

### Post by Stephen_d on 2009-04-01
Hello all, 

I am hoping someone can help with some errors I am receiving whilst trying to connect my ubuntu laptop to a netscreen firewall using a dial up VPN.

Here are the errors I am receiving
> Apr  1 14:15:03 mandrake racoon: INFO: @(#)ipsec-tools 0.7 ([http://ipsec-tools.sourceforge.net](http://ipsec-tools.sourceforge.net))
Apr  1 14:15:03 mandrake racoon: INFO: @(#)This product linked OpenSSL 0.9.8g 19 Oct 2007 ([http://www.openssl.org/](http://www.openssl.org/))
Apr  1 14:15:03 mandrake racoon: INFO: Reading configuration from "/etc/racoon/racoon.conf"
Apr  1 14:15:04 mandrake racoon: INFO: unsupported PF_KEY message REGISTER
Apr  1 14:15:05 mandrake last message repeated 2 times
Apr  1 14:15:05 mandrake racoon: INFO: Resize address pool from 0 to 255
Apr  1 14:15:05 mandrake racoon: ERROR: failed to bind to address 127.0.0.1[500] (Address already in use).
Apr  1 14:15:05 mandrake racoon: ERROR: failed to bind to address 10.46.25.203[500] (Address already in use).
Apr  1 14:15:05 mandrake racoon: ERROR: failed to bind to address ::1[500] (Address already in use).
Apr  1 14:15:05 mandrake racoon: ERROR: no address could be bound.

I am trying to connect via a vodafone 3g connection to the firewall.

any help is greatly appreciated


Stephen

---

### Post by chrisidc on 2009-07-30
[http://my.stargazer.at/2008/07/04/ipsec-between-linux-and-the-netscreen/](http://my.stargazer.at/2008/07/04/ipsec-between-linux-and-the-netscreen/)
[http://www.prolixium.com/netscreenlinux](http://www.prolixium.com/netscreenlinux)

if this doesn't work, let me know and I will give you more information, because I have a running configuration

---

