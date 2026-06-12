---
title: "Ubuntu 6.06 LTS proxy"
date: 2006-11-06
forum: Desktop Environments
---

### Post by whiteB on 2006-11-06
Can I use my ubuntu Desktop as my Internet gateway proxy Server.By using
 2 NIC cards...What all things should I do to work out this..

---

### Post by kidders on 2006-11-06
You can indeed. To configure your computer to be an internet gateway for other PCs, you need to set up NAT, which involves installing & configuring iptables. Thankfully, there are *plenty* of HOWTOs around :-)

Ideally, you would configure a static private address for your second network adapter and install DNS and DHCP servers for use by computers connected to it.

---

### Post by whiteB on 2006-11-06
I am using 2 Internet connection in my network..So, I need to set-up
 Proxy...Will squid work in UBUNTU ???

---

### Post by kidders on 2006-11-06
Yes :-)

Squid works on virtually all Linux and Linux-like platforms.

---

### Post by whiteB on 2006-11-06
Is there any other simple way to set-up this..

---

### Post by kidders on 2006-11-06
Using two internet connections isn't something I've ever actually tried, but it seems non-trivial to me :-( As far as I can see, you'll only ever really be able to use one of them at any single moment in time, so how to spread the load between them equitably depends on how you use your network.

If you're a heavy bittorrent user, for instance, you could use one for web browsing, and the other for torrents. You would use iptables to redirect traffic appropriately.

You may also be able to use cron to rotate ISPs from time to time.

Am I on the right track in terms of what you want to do, or do you have something more elabourate in mind?

---

### Post by whiteB on 2006-11-06
NOOOO...Actually I am planning to connect the 2 connections in to two different Computers..With browser configuration, we can point to either of the proxi..RIGHT ??
 Some times internet spped is varying for DSL, that is the reason I want
 share the load or use in this way...
  
 Some users will connect to connection 1 and some will connect to connection2. How you feel??:)

---

### Post by kidders on 2006-11-06
Hmmm.... I'd be inclined to control the load balancing centrally, rather than leaving it up to individual computers. I imagine it would get pretty tedious to have to tinker with the proxy settings on multiple machines all the time.

One option might be to run two copies of squid transparently, and use iptables to redirect users to one or other copy, based on their IP addresses. That way, a single computer would be in control of who used which internet connection. What do you think?

If it were me, I'd plug both DSL connections into the same PC to keep everything nice and neat :-)

---

