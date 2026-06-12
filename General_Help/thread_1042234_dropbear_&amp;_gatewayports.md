---
title: "dropbear &amp; gatewayports"
date: 2009-01-17
forum: General Help
---

### Post by patx on 2009-01-17
Hi to all
 
I administrate about 100 busybox set top box. To communicate with the set top box, i installed dropbear on ubuntu 7.10 so it is used as a relay for rewerse tunneling...
 
I made a cron script on the set top boxes to connect to a http serwer,download and read a flag if read 0=do nothing elif read=1 make rewerse tunnel using dropbear on the set top box to my ubuntu PC ( also using dropbear).
 
All works fine but local only... ssh -p(user port) root@localhost works fine on my ubuntu machine but...
 
If i try to connect to ssh -p(user port) root@UBUNTU_IP connecxion is refused
 
I read something about setting the gatewayports and that dropbear -a would probably fix this but i can't make it work...
 
Where do i set gatewayports for dropbear in ubuntu or how do i make my serwer public ?! 
 
Thankx

---

