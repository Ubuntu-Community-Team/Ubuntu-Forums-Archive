---
title: "Wired internet takes forever to connect"
date: 2011-11-29
forum: Desktop Environments
---

### Post by brandom21 on 2011-11-29
Hey everyone,

I am using ubuntu 11.10 on a custom desktop. When I upgraded I started to have issues with the wired internet connecting to various websites. When I restart, the problem goes away until I navigate to a few sites. Also, if I click on a link multiple times, it will sometimes connect faster.

Here are some configuration files.

/etc/resolv.conf:

nameserver 8.8.8.8
nameserver 8.8.4.4

/etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.7
network 192.168.1.0
netmask 255.255.255.0
gateway 192.168.1.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


/etc/nsswitch.conf:

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] mdns4 dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

ifconfig -a:


eth0      Link encap:Ethernet  HWaddr 00:1c:c0:24:e6:a6  
          inet addr:192.168.1.7  Bcast:0.0.0.0  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1099 errors:0 dropped:0 overruns:0 frame:0
          TX packets:834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:101550 (101.5 KB)  TX bytes:150750 (150.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2012 (2.0 KB)  TX bytes:2012 (2.0 KB)

tap0      Link encap:Ethernet  HWaddr 42:28:05:58:a9:87  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


The computer has:
Processor - Intel pentium 4 HT 3.2ghz
1gb - 2 512mb DDR2 533
500gb HDD
Intel 945PLRN Motherboard... 
using onboard LAN adapter, which is an Intel 82562GX

Any ideas? Need anymore information?

---

### Post by brandom21 on 2011-12-03
Help anyone? Still having this issue. It is really getting quite annoying. :(

---

### Post by Azyx on 2011-12-03
> **brandom21 said:**
> Help anyone? Still having this issue. It is really getting quite annoying. :(

Seems like a problem with nameserver? Is it normal to have 8.8.8.8 and 8.8.4.4 for nameserver? In my machines I user the routers /gateways adress (192.168.0.1) who get it from the ISP.

/Cheers

---

### Post by bluexrider on 2011-12-03
does your ISP provide you a (STATIC) IP otherwise it needs to be set to (DHCP) 

if you are going through a router it is unlikely a static set-up,  most routers, unless reserved are not set in this fashion.

---

### Post by brandom21 on 2011-12-03
> **bluexrider said:**
> does your ISP provide you a (STATIC) IP otherwise it needs to be set to (DHCP) 

if you are going through a router it is unlikely a static set-up,  most routers, unless reserved are not set in this fashion.


No, Charter does not provide me a static address. I do have it set up to Dynamically get the address in my routers settings. All of the other computers on my network work fine with the internet. It is only after upgrading from 11.04 to 11.10 that I am having this issue. 

I have read in some forums about realtek ethernet driver issues in the kernal, but my server has an Intel networking chipset.

---

### Post by Azyx on 2011-12-03
> **brandom21 said:**
> No, Charter does not provide me a static address. I do have it set up to Dynamically get the address in my routers settings. All of the other computers on my network work fine with the internet. It is only after upgrading from 11.04 to 11.10 that I am having this issue. 

I have read in some forums about realtek ethernet driver issues in the kernal, but my server has an Intel networking chipset.

What does:
```
nano /etc/resolv.conf
```
get you on the other computers? I don't know but 8.8.8.8 and 8.8.4.4 seems strange for me..?

---

### Post by brandom21 on 2011-12-03
> **Azyx said:**
> Seems like a problem with nameserver? Is it normal to have 8.8.8.8 and 8.8.4.4 for nameserver? In my machines I user the routers /gateways adress (192.168.0.1) who get it from the ISP.

/Cheers


Those are google's name servers. I use them on my router as well. I put them in the resolv.conf to try and fix the problem to no avail.

I tried going back to using my router as the nameserver, restart networking and it is still having the same issue.

---

### Post by brandom21 on 2011-12-03
> **Azyx said:**
> What does:
```
nano /etc/resolv.conf
```get you on the other computers? I don't know but 8.8.8.8 and 8.8.4.4 seems strange for me..?

Again, they are google's name servers.

My mac's resolv file points to my router, as does my server now.

---

### Post by oldtimer7777 on 2011-12-03
> **brandom21 said:**
> Again, they are google's name servers.

My mac's resolv file points to my router, as does my server now.

I would use a faster nameserver than the free ones from google..  I had this same problem when I was using their DNS server ....  OpenDNS is much better and still just as free. But naturally it depends where you live on the earth.

---

### Post by brandom21 on 2011-12-03
> **oldtimer7777 said:**
> I would use a faster nameserver than the free ones from google..  I had this same problem when I was using their DNS server ....  OpenDNS is much better and still just as free. But naturally it depends where you live on the earth.

Still have the same issue after switching to OpenDNS's servers. :(

---

### Post by oldtimer7777 on 2011-12-03
> **brandom21 said:**
> Still have the same issue after switching to OpenDNS's servers. :(

Here is what you do.. and it will save you the most frustration and time with something like this.

Look up the make and model of your router online.. Go to their web site..  Search for the free tech support phone number for that router on the manufacturer's web site.  They provide free support over the phone.  Try to get someone in Level II tech support to walk you through this configuration to work with your ISP.  They will certainly know, and you will have this resolved the fastest way possible too. They know linux. They don't charge for this. They can even test your connection from their end to make sure you have it correctly installed. Most people don't know it even exists.

---

