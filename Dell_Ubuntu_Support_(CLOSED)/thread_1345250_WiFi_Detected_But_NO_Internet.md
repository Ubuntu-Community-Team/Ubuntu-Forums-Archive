---
title: "WiFi Detected But NO Internet"
date: 2009-12-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kdi on 2009-12-03
Hi guys...

I'm on Dell Studio 1435. my wifi card is Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01).

karmic detects wireless networks at my office and connect successfully but when i open firefox, no internet connection (failed to contact server).

this only happen at my office. at home, i can surf internet through wifi.

this is the ifconfig output :

eth2      Link encap:Ethernet  HWaddr 0c:60:76:24:99:fe  
          inet6 addr: fe80::e60:76ff:fe24:99fe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:115968 errors:9 dropped:0 overruns:0 frame:184595
          TX packets:41734 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8378122 (8.3 MB)  TX bytes:3851146 (3.8 MB)
          Interrupt:16 Base address:0xc000

it's obvious there are errors in it.

i hope somebody might help. thanks in advance..:)

---

### Post by mikewhatever on 2009-12-04
Is that all of the output? According to that, you aren't connected, cause there is no IP address. Can you also try pinging google's IP when connected at the office:
```
ping -c4 74.125.67.100
```

---

### Post by efflandt on 2009-12-04
Looks like you do not quite have proper security settings.  Your work wireless router may have automatic or open association, but without proper security settings, you go nowhere.  That can happen if you slip a digit or character somewhere.

---

### Post by ugm6hr on 2009-12-05
> **mikewhatever said:**
> Is that all of the output? According to that, you aren't connected, cause there is no IP address.

Indeed, you are not connected at all.

Some detail re: security of network at work would help. Although, you'll probably have to ask your IT manager for help.

---

### Post by kdi on 2009-12-09
thanks guys for ur info. i'll see the IT staffs asap.:p

---

### Post by randumbtune on 2010-05-02
Hello dude, 
I use the same Laptop , and had same issue every time i install UBUNTU 
just use a Ethernet Cable , and wait for a while until everything settles down, and once you get connected to Internet , 
follow :

System>Administrator > Hardware Drivers 

and a window will open and tell you that restricted drivers are available , 
and then you will probably be  notified with available proprietary drivers for your Wifi module, just select any one of em , and continue, you will prolly see your wifi module working

---

### Post by pxwebdev on 2010-05-04
I had a similar issue with my 1720. I installed 10.04 but I had no wireless internet at all.  I even manually entered my info and it did not work.

Here is what I did to correct the issue:
1. Plug in a wired connection (lan cable)
2. Setup your ethernet connection for wired. (IE: ip, subnet or use DHCP)
3. Start up terminal
4. sudo apt-get update
5. sudo apt-get upgrade
6. Then go to system, administration, Restricted Drivers
7. Enable the broadcom sta driver for wireless. (Think thats the name. It will say the name and explain its the wireless driver.)
8. Reboot and reconfig your wireless access.

---

