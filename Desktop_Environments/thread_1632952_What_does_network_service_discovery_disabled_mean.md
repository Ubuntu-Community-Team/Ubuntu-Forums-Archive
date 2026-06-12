---
title: "What does network service discovery disabled mean?"
date: 2010-11-28
forum: Desktop Environments
---

### Post by ola on 2010-11-28
Every time i boot up i get an annoying message that says: Network service discovery disabled

What is that and how can I fix it?

---

### Post by germanix on 2010-11-30
It looks like avahi-daemon is also started when the network connection is established (/etc/network/if-up.d/avahi-daemon).
This notification is informing you that mDNS (Avahi) has been disabled. It's only used for a small number of applications that only work on the local network, it won't adversely affect your Internet connection or DNS.

The most well known use for mDNS is sharing music with Rhythmbox (or iTunes) over your LAN. It's an Apple technology, but it's largely been ignored in favour of uPNP or DLNA.
 

To disable it, you must edit the file /etc/default/avahi-daemon as root:

Code:
gksu gedit /etc/default/avahi-daemon
and add this line:
Code:
AVAHI_DAEMON_DETECT_LOCAL=0
or

(if you see this line: AHAVI_DAEMON_DETECT_LOCAL=1 then just change it to AHAVI_DAEMON_DETECT_LOCAL=0)

---

