---
title: "Ubuntu 9.04 with Dell GX260 network sharing problem after update"
date: 2009-07-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Clintster on 2009-07-15
HI all,
I have installed the Dell Ubuntu 9.04 on a Dell that I wish to share my network connection through to other computers, due to having a small hub that is already maxed out with no ports left. It works just fine until I run the updates through Update Manager, then I loose to connection sharing, The Dell can surf the web fine, the pc connected to it will not, though I can ping the outside world just fine. This didn't happen with the normal distro, only with the Dell distro. I was trying different firewalls with the normal distro and everytime I installed it I would loose the shared connection, tried both fwbuilder and firestarter. I gave up, then I found the Dell Distro and thought I would give it a try. I haven't installed a firewall on the Dell distro, haven't gotten that far. Just the updates. I have tried clearing the IPTABLES and UFW status is inactive. I'm kind of new to Linux as you might have guessed, though I have been playing with it for a little while and have it installed on another, better PC, triple boot, using GRUB with WINXP and Vista. Please Help tried searching the forums but couldn't find anything related to my problem.
 
EDIT: I am now trying the updates individually, 1 at a time with the most obvious updates first, hopefully I will get it figured out. If I do, I will post the solution.

---

### Post by Clintster on 2009-07-16
Update:
Found out it was NTPDATE that was causing the problem after running the updates from Software Manager. Does anybody know what changes this does that would effect the connection sharing like that. BTW the network settings were done using Network Manager.
 
Update: I guess I was wrong about that, dang, after loosing the share yet again, and another reinstallation, yet again. I'm not going to run any updates for awhile and see if I still loose the share. :(

---

