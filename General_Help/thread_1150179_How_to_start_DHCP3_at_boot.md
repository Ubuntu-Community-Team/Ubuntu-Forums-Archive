---
title: "How to start DHCP3 at boot"
date: 2009-05-05
forum: General Help
---

### Post by icarey on 2009-05-05
Hello,
I am using Ubuntu 9.04
How can I start DHCP3 at boot?
An /etc/init.d/dhcpd start works and I can connect from my clients

Thanks,
Ivan

---

### Post by dcstar on 2009-05-05
> **icarey said:**
> Hello,
I am using Ubuntu 9.04
How can I start DHCP3 at boot?
An /etc/init.d/dhcpd start works and I can connect from my clients

Thanks,
Ivan

Either manually make a link in the /etc/rc.2 directory or use one of the various tools that sets this up automagically.

---

### Post by Iowan on 2009-05-05
I'm a little surprised the startup didn't get set when the program was installed.

---

### Post by icarey on 2009-05-05
Resolved

I removed all entries from network manager and setup the interface in /etc/network/interfaces and added nameservers to /etc/reslov.conf

I checked for a link in the /etc/rc2.d to dhcp3-server.
Once I knew where all the start up scripts were I was able to investigate further.

Thanks to all for your assistance

Ivan

---

