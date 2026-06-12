---
title: "Internet works in VMWARE(XP) but not live cd?"
date: 2009-05-03
forum: General Help
---

### Post by dragonbeast25 on 2009-05-03
Currently im in vmware workstation running knoppix 6 i think and still on xp. P.S when i set it up i put bridged connection (Might be helpfull)

I have a Dsl modem (Speedtouch home)>connected to router(D-link WBR-1310)

DCHP i belive, My ip 192.168.0.100, submask 255.255.255.0, gw, 192.168.0.1

Recently ive ran into problems with the live CD when i boot it like boot it not in vmware but in boot menu, it goes everything works alright it goes it and all compiz works even no i have no graphics card its amazing ! but the issue is that it wont connect in knoppix. ok first it wont enable networking but it still trys to connect i can still access radio button on eth0, But i cant change any settings in manual or edit . When i run in vmware it auto maticly works because i think because my xp computer is connected already, what it shows is 2 computers ( I think its because its bridged, and yeah) my route in vmware im on now is here. Ill supply some more stuff for you guys.
P.S this is in the connection that is working

One more thing. Enable networking is not checked but it still works so thats not the problem

Ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:7d:71:f8  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe7d:71f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1321590 (1.2 MiB)  TX bytes:218367 (213.2 KiB)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Route/Netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

So ive supplyed much info as possible my main Os is Windows xp sp2, pro.

Please help me and thank you guys.

Had same problem in ubuntu.

---

### Post by dragonbeast25 on 2009-05-03
At least anyone no how to bridge connections in knoppix, and one more thing in live cd my dlink router does not pickup the livecd OS on linux distributions.

So some how we can enable it to reconize linux, and /or bridge connection, need support guys.

---

### Post by dragonbeast25 on 2009-05-03
bump

---

### Post by dragonbeast25 on 2009-05-03
please reply im going to be up in morning good night

---

### Post by dragonbeast25 on 2009-05-04
comon guys :(

---

### Post by dragonbeast25 on 2009-05-04
bump

---

