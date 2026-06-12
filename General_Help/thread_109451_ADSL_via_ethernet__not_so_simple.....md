---
title: "ADSL via ethernet : not so simple...."
date: 2005-12-28
forum: General Help
---

### Post by skaboss on 2005-12-28
Hello,

I used to connect to internet with my silly ADSL USB modem (thanks to eagle-usb driver). That perfectly worked until my last dist-upgrade (which apparently broke my driver forever :cry: )
So i decided to buy an ethernet modem (D-LINK DSL 300T), everybody saying ethernet is the real way to access internet under linux. This modem is supposed to be the simplest possible : no router, no wifi, just an ADSL modem.
And i must be dumb since i can't make my connection work...
So please help me before i get really nuts (and i swear i'm not so far from this !).
I first set up my modem via the web interface (accessible through [http://192.168.1.1)](http://192.168.1.1)). I just entered my login and password to connect to my ISP, and PPOE parameters. 
After several reboots, /etc/init.d/networking restart, and pints of Foster's, i still didn't manage to connect.
I even lost the connection to the web interface of my modem !
Here are some outputs that may give you a hint :
```
# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:76:40:03:3B
          inet addr:82.121.230.120  Bcast:82.121.230.120  Mask:255.255.255.255
          inet6 addr: fe80::20c:76ff:fe40:33b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5900 (5.7 KiB)  TX bytes:9816 (9.5 KiB)
          Interrupt:22 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:53739 (52.4 KiB)  TX bytes:53739 (52.4 KiB)
```

```
# tail /etc/network/interfaces
iface eth0 inet dhcp

iface dsl-provider inet ppp
provider dsl-provider

auto eth0
```

```
# tail /etc/resolv.conf
nameserver 80.10.246.130
```

I forgot to mention that pppoeconf fails, just saying something like this> Acces concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.

---

### Post by darth_vector on 2005-12-28
is the modem running a DHCP server? probably not. you eth0 ip and the modems ip do not match. edit /etc/network/interfaces as root and remove the

```
iface eth0 inet dhcp
```

and add a new entry like this:

```
iface eth0 inet static
<tab>address 192.168.1.2
<tab>netmask 255.255.255.0
<tab>gateway 192.168.1.1
```

and do an /etc/init.d/network restart. you should be good to go.

---

### Post by skaboss on 2005-12-28
Hello, and thanks a lot for your quick answer !
Actually, my modem is DHCP server (at least, that is what was enabled by default, and i left it on).
But i'm gonna try immediately your suggestion and let you know what happened.

---

### Post by skaboss on 2005-12-28
ok, i tried your solution, with no success, but thank you for your support anyway !
Would you have another suggestion ?

---

### Post by Ocxic on 2005-12-28
why do ppl always use the usb connection for there internet. 
switch to ethernet, it's easier to setup, and it's FASTER then usb is.
plus by using usb your puuting more strain on the usb hub making every other of you usb devices work slower.

---

### Post by darth_vector on 2005-12-28
can you post the output of:

ifconfig
route -n

also, can you ping 192.168.1.1 ?

---

### Post by Ocxic on 2005-12-28
try logging into your ADSL modem if you can get it IP address and check the settings.

NOTE: The IP address of your ADSL modem is NOT your computers IP address.

---

### Post by darth_vector on 2005-12-28
[QUOTE=skaboss]I first set up my modem via the web interface (accessible through [http://192.168.1.1)](http://192.168.1.1)).[/QUOTE]

thats the modems internal IP address, unless he has changed it.

---

### Post by skaboss on 2005-12-29
Thanks fo your posts.
I'm at work now, but i will post the outputs you suggested tonight.
In addition, you are right, 192.168.1.1 is the modem's internal IP, i didn't change it.

---

### Post by skaboss on 2005-12-29
Here i am again.

I reseted my modem and disabled the DHCP server option on my modem, and ifconfig looks better now : 
```

root@kubuntubox:~ # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:76:40:03:3B
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe40:33b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:346009 (337.8 KiB)  TX bytes:99824 (97.4 KiB)
          Interrupt:22 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:93268 (91.0 KiB)  TX bytes:93268 (91.0 KiB)

```

I can even access my modem's web interface again !

However, i still can't connect to any site, firefox saying  that it can not find the server.

Here is what route -n says : 
```

root@kubuntubox:~ # route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0


```

Last but not least, i finally managed to connect to the web under win xp, with this same modem, so i assume the modem is correctly set.

Seems like i'm almost done, so please keep helping me ! [-o<

---

### Post by darth_vector on 2005-12-29
you dont have a route set in the routing table. the following should fix that:

```
sudo route add default gw 192.168.1.1 dev eth0
```

---

### Post by skaboss on 2005-12-29
[QUOTE=darth_vector]you dont have a route set in the routing table. the following should fix that:

```
sudo route add default gw 192.168.1.1 dev eth0
```[/QUOTE]

!!!!! WOOOOWWW !!!!!

Thank you so much !!!!!
I'm finally writing this post from my kubuntu box thanks to your advices.
Thanks a lot 

Skaboss

---

### Post by darth_vector on 2005-12-29
no worries mate, enjoy ;)

---

