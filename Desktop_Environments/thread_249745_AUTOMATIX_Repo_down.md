---
title: "AUTOMATIX Repo down?"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Uncle Spellbinder on 2006-09-02
I've been getting this the past couple days:

```
Err http://www.getautomatix.com dapper Release.gpg
  Could not connect to www.getautomatix.com:80 (82.165.193.29), connection timed out
```

Same with attempting to reach the Automatix Websites [http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/) and [http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by andlinux21 on 2006-09-03
I just used the website 2 days ago on a fresh dapper install I don't know why your getting that error. I will see if I can access it when I go home in the morning

---

### Post by KageKeeper on 2006-09-03
Yep.

I am getting the same messages myself.

---

### Post by Uncle Spellbinder on 2006-09-03
> **KageKeeper said:**
> Yep.

I am getting the same messages myself.

Thanks for checking. I thought I was going mad.

---

### Post by azraelx401 on 2006-09-03
I got the same thing but it could be that there's a high flow of traffic on the server, the server cpu is high, or the server is down.  When I got the message I kept trying it over and over and eventually I got through.

---

### Post by arnieboy on 2006-09-03
[http://ubuntuforums.org/showpost.php?p=1455621&postcount=7](http://ubuntuforums.org/showpost.php?p=1455621&postcount=7)

---

### Post by Uncle Spellbinder on 2006-09-03
> **arnieboy said:**
> [http://ubuntuforums.org/showpost.php?p=1455621&postcount=7](http://ubuntuforums.org/showpost.php?p=1455621&postcount=7)

Thank you for the reply, *arnieboy*. Thanks to you and the Automatix team for the great work! Will be waiting patiently. :D

---

### Post by arnieboy on 2006-09-03
everything back up in top gear now.

---

### Post by boonybooni on 2006-09-04
hi you say that everything is working but i haven't been able to connect to "http://www.getautomatix.com" for last few days and still cant now. i really like automatix and really realy need it. can anyone point me in the right direction.thanx

---

### Post by arnieboy on 2006-09-05
> **boonybooni said:**
> hi you say that everything is working but i haven't been able to connect to "http://www.getautomatix.com" for last few days and still cant now. i really like automatix and really realy need it. can anyone point me in the right direction.thanx

the site is back up at full speed.. check ur internet conn..

---

### Post by Uncle Spellbinder on 2006-09-05
No problems here. Connecting to [http://www.getautomatix.com](http://www.getautomatix.com) just fine. Speedy, even.

---

### Post by boonybooni on 2006-09-05
my internet conection seems to be fine i can surf the net and use synaptic.
when i try to get the key for automatix i get the following:

tayyab@tayyabhost:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--13:35:58--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.1'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... failed: Connection refus ed.
 any ideas what im doing wrong? thanx for ur help

---

### Post by boonybooni on 2006-09-05
maybe this info will be useful:



tayyab@tayyabhost:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
tayyab@tayyabhost:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:17:8D:1A:99
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe8d:1a99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8241545 (7.8 MiB)  TX bytes:1130964 (1.0 MiB)
          Interrupt:217 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5664 (5.5 KiB)  TX bytes:5664 (5.5 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)




is there sumthing wrong with it?

---

### Post by sketchone on 2006-09-05
DNS problem maybe, i had the same problem a few days ago.

dont know if this helps but what i had to do to get automatix working was - in my router settings i had to add my ISP's DNS servers and also select not to use auto best found DNS.
Also in the Ubuntu networking settings add them in there.

---

### Post by boonybooni on 2006-09-05
thanx sketchone for your help, i tried it but sadly it didnt work, a bit lost here!:-?

---

### Post by boonybooni on 2006-09-08
got automatix working i think there was something wrong with my internet. today it just started working itself. im so happy. automatix is great

---

