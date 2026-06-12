---
title: "New port showing up after upgrade"
date: 2005-10-17
forum: Desktop Environments
---

### Post by stack445 on 2005-10-17
Hi all, here a nmap of my box after a breezy upgrade. :

PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
631/tcp   open  ipp
8888/tcp  open  sun-answerbook
10000/tcp open  snet-sensor-mgmt
32770/tcp open  sometimes-rpc3
32771/tcp open  sometimes-rpc5

Now some of the stuff i know what it is, like my ftp server, my ssh remote acces, webmin ( port 10000 ). Fot the smtp, i used to kill it manually, but it was there before. What bug me is the 8888 sun thing and the last two. What are those, they where not there before the upgrade ? 

Also i've read in the forum about firestarter ( iptable ) was on by default. Is there a way to shut it down. I dont seem to be able to locate it in the process list ( no ip table running or something like that) . I've notice that i'm not able to log in in my ftp remotly since the upgrade, and azureus dont download anymore.  Is it best to actualy set rules for ftp, azureus, and ssh with firestarter than disable the whole firewall ? I already have a firewall in my cable router. 

Thanks for youre idea and reply ...

stack

---

### Post by flibble on 2005-10-24
Hmmm... I have port 8888 open also. 

I'd guess that the 'sun-answerbook' thing is just nmap mislabelling the port.

running amap on that port gives:

amap v4.7 ([www.thc.org](www.thc.org)) started at 2005-10-24 21:42:49 - APPLICATION MAP mode

Total amount of tasks to perform in plain connect mode: 17
Waiting for timeout on 17 connections ...
Protocol on 192.168.1.2:8888/tcp (by trigger sap-r3) matches http

...which is interesting. I don't see a http server running. I'll look into this further when I have some time.

Anyone know what's going on here?

---

