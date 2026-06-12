---
title: "Net Connection problem"
date: 2009-05-25
forum: General Help
---

### Post by nehagupta on 2009-05-25
Hi I just start to work on ubuntu 7.1.0
I have problem with net connection ( i have set static ip address ). Most of the time net connection doesnt work and some time it quickly connects. Moreover sometimes it only allows 1 or 2 sites and dont connect to other site even not to google.

---

### Post by nehagupta on 2009-05-25
Hi i want to add one more thing that my net connection work properly on windows xp

---

### Post by albinootje on 2009-05-25
> **nehagupta said:**
> Hi I just start to work on ubuntu 7.1.0

Please use ubuntu 8.04, because 7.10 is no longer supported.
-> [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)
> 
I have problem with net connection ( i have set static ip address ). Most of the time net connection doesnt work and some time it quickly connects. Moreover sometimes it only allows 1 or 2 sites and dont connect to other site even not to google.

Can you post the output of the following from a terminal in your Ubuntu installation :
```

cat /etc/resolv.conf

```

---

### Post by nehagupta on 2009-05-25
outpout of command cat /etc/resolv.conf 
nameserver 192.168.1.1

---

### Post by nehagupta on 2009-05-25
I followed the link [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades) but problem is that for upgrade i need connection. But its  opening only 1-2 sites and nothing :(

---

### Post by albinootje on 2009-05-25
> **nehagupta said:**
> outpout of command cat /etc/resolv.conf 
nameserver 192.168.1.1

Okay, can you set up your Network Manager settings to use the DNS servers of OpenDNS ?

Instructions here :
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by nikhilbhardwaj on 2009-05-25
are you using mtnl ??
if so then it may be DHCP and not Static

---

