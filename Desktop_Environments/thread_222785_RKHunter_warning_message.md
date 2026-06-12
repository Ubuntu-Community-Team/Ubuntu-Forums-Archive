---
title: "RKHunter warning message"
date: 2006-07-25
forum: Desktop Environments
---

### Post by teeleef on 2006-07-25
Ladies & Gents,  I ran RKHunter to check my system, when I came upon this:-

* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)  /etc/.java (directory)


As I don't understand the inner working of Ubuntu or RKHunter I was concerned if anything was amiss or if my Linux box had been compromised?



Teeleef

---

### Post by ardchoille on 2006-07-25
I have Ubuntu 6.06 on 11 computers. rkhunter is one of the first things I run after a fresh install and before connecting the box to anything that is network related. I have seen these same rkhunter messages on every Ubuntu computer that I have run rkhunter on and I don't feel this particular message is anything to be alarmed about. If you are still worried, you can go to [http://www.rootkit.nl/contact/](http://www.rootkit.nl/contact/) and fill out the contact info to contact the rkhunter author.

---

### Post by teeleef on 2006-07-25
thanks ardchoille !!!  Funny thing is I ran chkrootkit and get the following:-

Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth1: PACKET SNIFFER(/sbin/dhclient3[4160])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted


Was wondering if the two errors were linked???

teeleef

---

### Post by ardchoille on 2006-07-25
> **teeleef said:**
> thanks ardchoille !!!  Funny thing is I ran chkrootkit and get the following:-

Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth1: PACKET SNIFFER(/sbin/dhclient3[4160])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted


Was wondering if the two errors were linked???

teeleef

I have seen this on my Ubuntu boxes too, I run rkhunter, chkrootkit, tripwire and a few other apps before connecting a new computer. If these are real problems, then they are being shipped with Ubuntu ISO's. I wouldn't worry about them, though.

---

### Post by revertex on 2006-07-25
> **teeleef said:**
> 
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------


why these files are hidden?
the only reasonable file is /etc/.pwd.lock, i can't see the point for the others
why a hidden java file inside /etc?
amyway, if you want to get rid of these errors edit /etc/rkhunter.conf, the file is pretty self explanatory.

---

### Post by mordi on 2006-08-12
I was getting the same warning with chkrootkit

Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth1: PACKET SNIFFER(/sbin/dhclient3[3685]

after some research I found out that dhclient obtains the ip from the router or internet provider. so I did a little test and I switched in networking->eth1->properties->connection settings from dhcp to static ip.  I rescanned and the warning was gone. 

Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth1: not promisc and no packet sniffer sockets

so I guess if there was a problem, switching from dhcp to static ip would not make any difference.

---

