---
title: "Can not connect to internet"
date: 2006-07-16
forum: Desktop Environments
---

### Post by - P u r p l 3 - on 2006-07-16
I'm new to Linux. I don't know whether is here the right place to post my problem. Just have a try. no harm:) 

I have installed ubuntu 6.06 in my desktop and everything works fine except no internet connection. In my previous attempt few months ago, where i tried ubuntu 5.10 , i was able to go online. Wonder why? 

Currently i'm using Prolionk Hurricane 9000P router. Hope it helps to figure out the problem. Thanks in advance :D

---

### Post by Paerez on 2006-07-16
ok, open up a terminal (Applications -> Accessories -> Terminal) and type in the following, then paste all of the terminal content into this thread.
```
sudo ifconfig eth0
sudo dhclient eth0
```
That is if you are using wired internet. If you use wireless, change "eth0" to "eth1".

---

### Post by immesys on 2006-07-16
Not sure if your problem is already solved or not but I had a problem where firefox would time out even when connected to the internet. If so.. open firefox and type about:config in your address bar. Then type ipv6 into the filter box. There should be only one.. something about disable dns ipv6 etc... make sure it is set to true.

Note that there are fanatics out there that say that if ipv6 is causing trouble then it is a network config error but hey.. if this solves the problem then it solves the problem.

You can also further disable ipv6 on your entire system. Can't remember offhand but there is a thread on these forums somewhere.

---

### Post by eMuNiX on 2006-07-16
Not sure if this helps but there is a bug in the firmware for my router which prevents Linux from receiving DNS servers, it works fine in XP, but fails with Linux.  The way around it is to manually input the DNS servers for your ISP into the router config.  Perhaps this is worth a try.

---

