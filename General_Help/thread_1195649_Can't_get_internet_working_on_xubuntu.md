---
title: "Can't get internet working on xubuntu"
date: 2009-06-24
forum: General Help
---

### Post by watdafuk on 2009-06-24
I installed xubuntu on my old laptop and I can't get it to connect to the internet. I am using a  broadband wired connection and it seems to recognize the ethernet card but keeps saying "internet connection not connected". I don't have network manager, but when I right click on the little network icon and go to edit (or something I don't remember the exact name) it takes me to a "network configuration" window. And in that window under "wired" it shows "eth0", so I click on that and click edit and it shows a MAC address for it but it doesn't show any IP or DCHP addresses for it. 

How do I connect to the internet? I've searched through yahoo answers, google, and the ubuntu forums but with no luck. I have no clue why it's not working. 

Also when I look at the "how to connect to internet" instructions that comes with xubuntu it says to go to applications -> system -> network manager and then edit properties but there is no network manager!

Thanks.

---

### Post by zvacet on 2009-06-24
Try with **dsl** option.

---

### Post by nexes128 on 2009-06-24
Well if your dsl modem normally supply's you with an ip address with out the need for a password (i.e. acts like a router) you could just add the dhcp option to the interfaces file.

Open up a terminal and do the following
```
sudo nano /etc/network/interfaces
```

edit the eth0 entries to look like this (DO NOT CHANGE ANYTHING ELSE)

```
auto eth0
iface eth0 inet dhcp
```

hit Ctrl-X then y to save, then restart the network by doing the following:
```
sudo /etc/init.d/networking restart
```

You should see the system request an IP through DHCP, once thats done type ifconfig and eth0 should have an address(listed under "inet addr").

---

### Post by watdafuk on 2009-07-01
Thanks for your replies but it's still not working.

nexes128, I tried what you said and it didn't work. Not only does my internet still not work but when I restarted my computer the little network icon doesn't even show up anymore.

zvacet, I don't know what you mean by try with dsl option.

I don't think I have dsl anyways, because my internet is not connected through a phone line it is connected through a cable tv wire. My internet service is with charter communications.

Here is what comes up when I type ifconfig in the terminal:

paul@paul-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:9d:81:9e:a9
        inet6 addr: fe80::20d:9dff:fe81:9ea9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2263791 (2.2 MB)  TX bytes:11697 (11.6 KB)
          Interrupt:11 Base address:0x8000

eth0:avahi Link encap:Ethernet  HWaddr 00:0d:9d:81:9e:a9
        inet addr:169.254.8.144  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10068 (10.0 KB)  TX bytes:10068 (10.0 KB)

and when I try to ping xubunut.com it says "unkown host xubunut.com"

Also, I have a program called network configuration but no program called network manager.

The only reason I want to connect to the internet is because I bought the "You can code" magazine and am trying to get VirtualBox working. But I need to install the libstdc++5 library. Does anyone know how I can install that library without using the internet? Can I download it onto a flash drive and copy it to my laptop or something?

Thanks again.

---

