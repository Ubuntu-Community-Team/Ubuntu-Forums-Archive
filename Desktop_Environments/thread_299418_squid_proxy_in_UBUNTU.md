---
title: "squid proxy in UBUNTU"
date: 2006-11-14
forum: Desktop Environments
---

### Post by whiteB on 2006-11-14
Can I use my UBUNTU 6.06 desktop as my squid proxy server.By adding one
 more network card for Adsl link..
 The configuration file is in /etc/squid..??
 How can I start the squid service...??

---

### Post by Faheem on 2006-11-21
Hi

Yes to my knowledge you can use squid as a proxy on ubuntu. Make sure it is installed first. Either use the apt-get to fetch it or download the tarball from [http://www.squid-cache.org/](http://www.squid-cache.org/), get the latest stable release. Compile it and install it and by default it should use your default gateway as setup in your network config

---

