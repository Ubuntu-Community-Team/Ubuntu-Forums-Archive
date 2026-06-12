---
title: "NMap &amp; IP"
date: 2005-09-04
forum: Desktop Environments
---

### Post by ryke on 2005-09-04
Hi,

Two questions..

- to perform a port scan with Nmap, which is the IP? : the router's IP? the internet connection's IP? my LAN's IP?... has the scan to be performed as a root?

- is there any way to know which is my internet connection's IP?

thanx

---

### Post by KingBahamut on 2005-09-04
[QUOTE=ryke]Hi,

Two questions..

- to perform a port scan with Nmap, which is the IP? : the router's IP? the internet connection's IP? my LAN's IP?... has the scan to be performed as a root?

- is there any way to know which is my internet connection's IP?

thanx[/QUOTE]


nmap -vvv x.x.x.x 

where x will equal the IP you want to scan. Yes you have to be root to do a full scan. Syn scan recommended. If you have issues with running Nmap from command line, apt-get install nmapfe , the graphical front-end, But you will still need to be root. 

Whats your LAN Arch look like? you can most likely go to [http://checkip.dyndns.org](http://checkip.dyndns.org) and it will tell you what your public address is.

---

### Post by ryke on 2005-09-05
thanx for your answers  O:) 

however, i don't understand one thing... in my router, I've opened 2 ports (1 tcp and 1 udp, for amule) forwarded to my pc... but nmap doesn't tell me anything about that (it doesn't matter if I scan my router's IP or my PC's IP... is that ok?

thanx

---

### Post by KingBahamut on 2005-09-05
[QUOTE=ryke]thanx for your answers  O:) 

however, i don't understand one thing... in my router, I've opened 2 ports (1 tcp and 1 udp, for amule) forwarded to my pc... but nmap doesn't tell me anything about that (it doesn't matter if I scan my router's IP or my PC's IP... is that ok?

thanx[/QUOTE]
 apt-get install etherape 

run etherape as root. 

then 

run Amule, get some active connections going, and youll see etherape light up like a christmas tree....this being the sign your getting the traffic.

---

### Post by ryke on 2005-09-05
yes, it seems a christmas' tree and it's really curious :) 
however, with etherape i can't see the numbers of the opened pots.

---

