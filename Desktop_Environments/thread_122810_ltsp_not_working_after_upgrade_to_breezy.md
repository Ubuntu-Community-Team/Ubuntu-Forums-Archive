---
title: "ltsp not working after upgrade to breezy"
date: 2006-01-28
forum: Desktop Environments
---

### Post by tariqf on 2006-01-28
I had ltsp working perfectly in hoary until I did I dist-upgrade to breezy. Now my network boot clients get error:

ERROR! No root path specified. Please check your DHCP server configuration.
kernel panic ...

My dhcpd.conf has not changed since the upgarde and does have "option root-path" included which used to work fine. it has,

option root-path             "192.168.2.10:/opt/ltsp/i386";

I have also confirmed that the root path exists.

Please can anyone help?

---

### Post by tariqf on 2006-01-29
Ok I downdraded dhcp3-server to dhcpd and it now works fine!

---

