---
title: "CIsco VPN problems"
date: 2009-05-12
forum: General Help
---

### Post by frankh on 2009-05-12
I'm struggling to get the Cisco VPN client to work in Ubuntu 8.10.

I have one windows machine running the windows client, and this machine connects fine to my work's VPN, and can access the internal web pages.

On my Ubuntu box, I'm able to connect fine with the Linux Cisco VPN client, and everything seems fine, except I cannot connect to the local web pages, or ping the local server(s).

ifconfig shows the cipsec0 interface

netstat -rn shows the following:

```

[FONT="Courier New"][SIZE="2"]Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
193.71.68.2     10.0.0.1     255.255.255.255 UGH   0 0      0 eth0
172.28.0.0       0.0.0.0      255.255.0.0     U     0 0      0 cipsec0
0.0.0.0             172.28.1.3   0.0.0.0         UG    0 0      0 cipsec0 [/SIZE][/FONT]

```

Anyone got any ideas?

---

