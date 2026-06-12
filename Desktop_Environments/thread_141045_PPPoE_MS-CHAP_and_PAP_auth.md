---
title: "PPPoE MS-CHAP and PAP auth"
date: 2006-03-07
forum: Desktop Environments
---

### Post by hristo.doynov on 2006-03-07
Hi, everyone.

I am complete newby, so please be patient with me. I ran the pppoeconf and managed to connect to my ISP. There seems to be some problem, as when looking at the log, it seems to try random times MS-CHAP auth (which fails) and then switch to PAP (which succeeds).

This is my provider conf file:
> # Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
show-password
refuse-chap
require-pap
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#mru 1492
usepeerdns
plugin rp-pppoe.so eth0
user "hdoinov"


and the logs of several connections I made (please take a look at the time - those are consecutive attempts)

> xpucmo@doynovi:/etc/ppp/peers$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
xpucmo@doynovi:/etc/ppp/peers$ plog -f
Mar  7 19:32:19 localhost pppd[7422]: Connection terminated.
Mar  7 19:32:19 localhost pppd[7422]: Exit.
Mar  7 19:32:28 localhost pppd[9220]: Plugin rp-pppoe.so loaded.
Mar  7 19:32:28 localhost pppd[9222]: pppd 2.4.3 started by root, uid 0
Mar  7 19:32:28 localhost pppd[9222]: PPP session is 476
Mar  7 19:32:28 localhost pppd[9222]: Using interface ppp0
Mar  7 19:32:28 localhost pppd[9222]: Connect: ppp0 <--> eth0
Mar  7 19:32:28 localhost pppd[9222]: Couldn't increase MTU to 1500
Mar  7 19:32:28 localhost pppd[9222]: Couldn't increase MRU to 1500
Mar  7 19:32:31 localhost pppd[9222]: Couldn't increase MTU to 1500
Mar  7 19:32:31 localhost pppd[9222]: PAP authentication succeeded
Mar  7 19:32:31 localhost pppd[9222]: peer from calling number 00:13:D4:82:CA:B6 authorized
Mar  7 19:32:31 localhost pppd[9222]: replacing old default route to eth0 [10.100.16.1]
Mar  7 19:32:31 localhost pppd[9222]: Cannot determine ethernet address for proxy ARP
Mar  7 19:32:31 localhost pppd[9222]: local  IP address 212.21.150.222
Mar  7 19:32:31 localhost pppd[9222]: remote IP address 212.21.133.33
Mar  7 19:32:31 localhost pppd[9222]: primary   DNS address 212.21.128.4
Mar  7 19:32:31 localhost pppd[9222]: secondary DNS address 212.21.128.10
...
xpucmo@doynovi:/etc/ppp/peers$ sudo poff
xpucmo@doynovi:/etc/ppp$ sudo pon intech
Plugin rp-pppoe.so loaded.
xpucmo@doynovi:/etc/ppp$ plog -f
Mar  7 19:37:40 localhost pppd[9345]: PPP session is 862
Mar  7 19:37:40 localhost pppd[9345]: Using interface ppp0
Mar  7 19:37:40 localhost pppd[9345]: Connect: ppp0 <--> eth0
Mar  7 19:37:40 localhost pppd[9345]: Couldn't increase MTU to 1500
Mar  7 19:37:40 localhost pppd[9345]: Couldn't increase MRU to 1500
Mar  7 19:37:40 localhost pppd[9345]: Couldn't increase MRU to 1500
Mar  7 19:37:40 localhost pppd[9345]: MS-CHAP authentication failed: bad username or password
Mar  7 19:37:40 localhost pppd[9345]: Couldn't increase MTU to 1500
Mar  7 19:37:40 localhost pppd[9345]: Couldn't increase MRU to 1500
Mar  7 19:37:40 localhost pppd[9345]: Connection terminated.
Mar  7 19:38:10 localhost pppd[9345]: PPP session is 327
Mar  7 19:38:10 localhost pppd[9345]: Using interface ppp0
Mar  7 19:38:10 localhost pppd[9345]: Connect: ppp0 <--> eth0
Mar  7 19:38:10 localhost pppd[9345]: Couldn't increase MTU to 1500
Mar  7 19:38:10 localhost pppd[9345]: Couldn't increase MRU to 1500
Mar  7 19:38:13 localhost pppd[9345]: Couldn't increase MTU to 1500
Mar  7 19:38:13 localhost pppd[9345]: Couldn't increase MRU to 1500
Mar  7 19:38:13 localhost pppd[9345]: PAP authentication succeeded
Mar  7 19:38:13 localhost pppd[9345]: peer from calling number 00:13:D4:82:C9:7F authorized
Mar  7 19:38:13 localhost pppd[9345]: replacing old default route to eth0 [10.100.16.1]
Mar  7 19:38:13 localhost pppd[9345]: Cannot determine ethernet address for proxy ARP
Mar  7 19:38:13 localhost pppd[9345]: local  IP address 212.21.141.73
Mar  7 19:38:13 localhost pppd[9345]: remote IP address 212.21.133.33
Mar  7 19:38:13 localhost pppd[9345]: primary   DNS address 212.21.128.4
Mar  7 19:38:13 localhost pppd[9345]: secondary DNS address 212.21.128.10

xpucmo@doynovi:/etc/ppp$ sudo poff
xpucmo@doynovi:/etc/ppp$ sudo pon intech
Plugin rp-pppoe.so loaded.
xpucmo@doynovi:/etc/ppp$ plog -f
Mar  7 19:46:09 localhost pppd[9721]: PPP session is 949
Mar  7 19:46:09 localhost pppd[9721]: Using interface ppp0
Mar  7 19:46:09 localhost pppd[9721]: Connect: ppp0 <--> eth0
Mar  7 19:46:09 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:46:09 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:46:09 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:46:10 localhost pppd[9721]: MS-CHAP authentication failed: bad username or password
Mar  7 19:46:10 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:46:10 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:46:10 localhost pppd[9721]: Connection terminated.
Mar  7 19:46:40 localhost pppd[9721]: PPP session is 953
Mar  7 19:46:40 localhost pppd[9721]: Using interface ppp0
Mar  7 19:46:40 localhost pppd[9721]: Connect: ppp0 <--> eth0
Mar  7 19:46:40 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:46:40 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:46:40 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:46:43 localhost pppd[9721]: MS-CHAP authentication failed: bad username or password
Mar  7 19:46:43 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:46:43 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:46:43 localhost pppd[9721]: Connection terminated.
Mar  7 19:47:13 localhost pppd[9721]: PPP session is 959
Mar  7 19:47:13 localhost pppd[9721]: Using interface ppp0
Mar  7 19:47:13 localhost pppd[9721]: Connect: ppp0 <--> eth0
Mar  7 19:47:13 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:47:13 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:47:13 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:47:15 localhost pppd[9721]: MS-CHAP authentication failed: bad username or password
Mar  7 19:47:15 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:47:15 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:47:15 localhost pppd[9721]: Connection terminated.
Mar  7 19:47:45 localhost pppd[9721]: PPP session is 965
Mar  7 19:47:45 localhost pppd[9721]: Using interface ppp0
Mar  7 19:47:45 localhost pppd[9721]: Connect: ppp0 <--> eth0
Mar  7 19:47:45 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:47:45 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:47:45 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:47:47 localhost pppd[9721]: MS-CHAP authentication failed: bad username or password
Mar  7 19:47:47 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:47:47 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:47:47 localhost pppd[9721]: Connection terminated.
Mar  7 19:48:17 localhost pppd[9721]: PPP session is 972
Mar  7 19:48:17 localhost pppd[9721]: Using interface ppp0
Mar  7 19:48:17 localhost pppd[9721]: Connect: ppp0 <--> eth0
Mar  7 19:48:17 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:48:17 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:48:17 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:48:18 localhost pppd[9721]: MS-CHAP authentication failed: bad username or password
Mar  7 19:48:18 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:48:18 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:48:18 localhost pppd[9721]: Connection terminated.
Mar  7 19:48:48 localhost pppd[9721]: PPP session is 978
Mar  7 19:48:48 localhost pppd[9721]: Using interface ppp0
Mar  7 19:48:48 localhost pppd[9721]: Connect: ppp0 <--> eth0
Mar  7 19:48:48 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:48:48 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:48:48 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:48:51 localhost pppd[9721]: MS-CHAP authentication failed: bad username or password
Mar  7 19:48:51 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:48:51 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:48:51 localhost pppd[9721]: Connection terminated.
Mar  7 19:49:21 localhost pppd[9721]: PPP session is 984
Mar  7 19:49:21 localhost pppd[9721]: Using interface ppp0
Mar  7 19:49:21 localhost pppd[9721]: Connect: ppp0 <--> eth0
Mar  7 19:49:21 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:49:21 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:49:21 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:49:24 localhost pppd[9721]: MS-CHAP authentication failed: bad username or password
Mar  7 19:49:24 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:49:24 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:49:24 localhost pppd[9721]: Connection terminated.
Mar  7 19:49:54 localhost pppd[9721]: PPP session is 990
Mar  7 19:49:54 localhost pppd[9721]: Using interface ppp0
Mar  7 19:49:54 localhost pppd[9721]: Connect: ppp0 <--> eth0
Mar  7 19:49:54 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:49:54 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:49:54 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:49:56 localhost pppd[9721]: MS-CHAP authentication failed: bad username or password
Mar  7 19:49:56 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:49:56 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:49:56 localhost pppd[9721]: Connection terminated.
Mar  7 19:50:26 localhost pppd[9721]: PPP session is 995
Mar  7 19:50:26 localhost pppd[9721]: Using interface ppp0
Mar  7 19:50:26 localhost pppd[9721]: Connect: ppp0 <--> eth0
Mar  7 19:50:26 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:50:26 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:50:26 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:50:27 localhost pppd[9721]: MS-CHAP authentication failed: bad username or password
Mar  7 19:50:27 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:50:27 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:50:27 localhost pppd[9721]: Connection terminated.
Mar  7 19:50:57 localhost pppd[9721]: PPP session is 32
Mar  7 19:50:57 localhost pppd[9721]: Using interface ppp0
Mar  7 19:50:57 localhost pppd[9721]: Connect: ppp0 <--> eth0
Mar  7 19:50:57 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:50:57 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:51:00 localhost pppd[9721]: Couldn't increase MTU to 1500
Mar  7 19:51:00 localhost pppd[9721]: Couldn't increase MRU to 1500
Mar  7 19:51:00 localhost pppd[9721]: PAP authentication succeeded
Mar  7 19:51:00 localhost pppd[9721]: peer from calling number 00:13:D4:82:CA:B6 authorized
Mar  7 19:51:00 localhost pppd[9721]: replacing old default route to eth0 [10.100.16.1]
Mar  7 19:51:00 localhost pppd[9721]: Cannot determine ethernet address for proxy ARP
Mar  7 19:51:00 localhost pppd[9721]: local  IP address 212.21.146.32
Mar  7 19:51:00 localhost pppd[9721]: remote IP address 212.21.133.33
Mar  7 19:51:00 localhost pppd[9721]: primary   DNS address 212.21.128.4
Mar  7 19:51:00 localhost pppd[9721]: secondary DNS address 212.21.128.10


Please give me some hint as for how to configure the PPPoE connection to start with PAP auth (if you think that is the problem), because sometimes it takes forever for the connection to be established, or it even doesn't connect.

Thanks in advance, 

Hristo Doynov.

---

### Post by noswal on 2006-03-14
Have you tried taking out the comments?
lcp-echo-interval 30
lcp-echo-failure 4

mtu 1500
mru 1492

---

### Post by hristo.doynov on 2006-03-15
[QUOTE=noswal]Have you tried taking out the comments?
lcp-echo-interval 30
lcp-echo-failure 4

mtu 1500
mru 1492[/QUOTE]

Yep, tried that. No use at all. Actualy I wasn't paying enough attention to this thread as a guy that lives close to me and uses the same provider was complaining about exactly the same problem - random number unsuccesfull connection tries (MS-CHAP auth failed message) and then either connecting using PAP or quitting without connection. He claims to have solved the problem using the rp-pppoe and I will try to install it. Unfortuanately I was unable to find a debian distribution so tonight I will install it out of RPM...

Thanks for your reply and best regards, 

Hristo Doynov.

---

