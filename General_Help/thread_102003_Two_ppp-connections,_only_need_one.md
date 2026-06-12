---
title: "Two ppp-connections, only need one"
date: 2005-12-11
forum: General Help
---

### Post by mexp on 2005-12-11
Upgraded to Breezy, and pppoe didn't work first so I re-ran pppoeconf. Fine, got pppoe running, but as a result there are two ppp connections making the same connection to same isp, ppp0 and ppp1. 

As a result, routing gets confused (or something else happens and the DNS resolving slows down).

*How do I delete or disable one of the started ppp-connections?* I haven't been able to find it *anywhere* in /etc/ppp, not in forums nor on IRC...

Please help!!!

---

### Post by mexp on 2005-12-11
Here's what ifconfig says:

ppp0      Link encap:Point-to-Point Protocol
         inet addr:80.XX.199.77  P-t-P:80.XX.199.1  Mask:255.255.255.255
         UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
         RX packets:217 errors:0 dropped:0 overruns:0 frame:0
         TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:3
         RX bytes:58063 (56.7 KiB)  TX bytes:36501 (35.6 KiB)

ppp1      Link encap:Point-to-Point Protocol
         inet addr:80.XX.199.79  P-t-P:80.XX.199.1  Mask:255.255.255.255
         UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
         RX packets:21130 errors:0 dropped:0 overruns:0 frame:0
         TX packets:20300 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:3
         RX bytes:1202959 (1.1 MiB)  TX bytes:2051404 (1.9 MiB)

---

### Post by theturner on 2006-01-02
Same problem here. I need to 'poff dsl-provider' and pon again.

I set firestarter to start at boot, could it have something to do with that?

---

### Post by andytof47 on 2007-02-03
I have this same problem aswell


How do we get rid of it??????


There should be someone who can help


It's not just one person


BUMP.................Please

---

