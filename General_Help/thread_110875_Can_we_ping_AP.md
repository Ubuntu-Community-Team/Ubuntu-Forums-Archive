---
title: "Can we ping AP?"
date: 2005-12-31
forum: General Help
---

### Post by shoshu on 2005-12-31
I have a question:
I know how many APs I can associate with by key in "iwlist".
If we want to know every AP's ping delay, can we ping every AP without 
associate with it?
or is there any command we can use to know AP's ping delay?
Thanks a lot:) !

---

### Post by jdong on 2005-12-31
I don't think there's a command for doing a raw ping of an AP, though surely you can hack one up in C pretty fast if you have good knowledge of how the Linux kernel wireless stack works.

---

### Post by Lambert on 2005-12-31
I don't believe there is as there needs to be a path for the packet to travel along. If there's no connection there's no path.

The distance or a wireless router is so short the ping time in miliseconds is never going to be that different between routers.

Also a ping can have such a various spread it's not a good way to test which router is best. I'm no more then 12 feet from my router and this is a ping spread for me.

64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=2.00 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=127 time=2.03 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=127 time=43.1 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=127 time=60.7 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=127 time=83.8 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=127 time=4.39 ms

This next set goes through 16 hops 1,000s of miles away and you can see that the lowest ping is only 7ms different then my greatest ping to a router only 12 ft away.

64 bytes from gentoo.ubuntu.com (82.211.81.130): icmp_seq=7 ttl=46 time=100 ms
64 bytes from gentoo.ubuntu.com (82.211.81.130): icmp_seq=8 ttl=46 time=90.6 ms
64 bytes from gentoo.ubuntu.com (82.211.81.130): icmp_seq=9 ttl=46 time=89.8 ms
64 bytes from gentoo.ubuntu.com (82.211.81.130): icmp_seq=10 ttl=46 time=105 ms

---

### Post by jdong on 2005-12-31
[QUOTE=Lambert]I don't believe there is as there needs to be a path for the packet to travel along. If there's no connection there's no path.
[/quote]

Well, you can temporarily "associate" (if you even consider it that) just to send the AP a few random raw 802.11 packets and see how long it takes for the router to reply (error packets primarily).
> 
The distance or a wireless router is so short the ping time in miliseconds is never going to be that different between routers.

Perhaps if one AP is extremely loaded or very low capacity, it'll show up in these simplistic tests. I really doubt it; I don't see much use for these types of ping tests.


Even if an AP responds well to ping packets, if the WAN connection is sucky there's no way to tell unless you go on the network.

Finally, **BE WARNED**: Some jurisdictions have extremely retarded/restrictive laws regarding wireless networks and unauthorized access, and actually enforce these on extremely sketchy/spoofable evidence. Make sure you know what you're getting yourself in to.

---

