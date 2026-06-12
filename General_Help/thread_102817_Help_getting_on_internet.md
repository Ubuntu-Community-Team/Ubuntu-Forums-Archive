---
title: "Help getting on internet"
date: 2005-12-12
forum: General Help
---

### Post by indeepthought on 2005-12-12
I can't seem to get access to the internet.  I initially intsalled Debian "sarge" installation and i was able to jump on mozilla and download other components.  I heard the ubuntu variation might be a better choice for e new linux user so i installed it instead.  I'm able to see windows computers via network so  I am sure i have some form of network connectivity, but i am at a loss as to why I am unable to access internet.  I currently have it set to a static IP.  I tried using auto DHCP but that did not work anyway.  Since we need this server to be static IP anyway, i might as well start from there anyway.  For those who have not read my other posts, please forgive my lack of knowledge on linux.

---

### Post by amohanty on 2005-12-12
Are you using a router with dhcp?
Is the static ip setup as static ip in the router?

post the output of:

```
ifconfig
ps aux | grep dhclient
cat /etc/hosts
cat /etc/network/interfaces

```

Each of the above is a separate command. Run each one and post the output.

---

### Post by mherring on 2005-12-12
Add to the previous input---

If you do have a router, can you ping it? can you log on to it's admin page?

---

### Post by indeepthought on 2005-12-14
i am typing this from handwritten notes from the screen so forgive any formatting issues:

results of ifconfig:

eth0  Link encap:Ethernet  HWaddr 00:02B3:0A:37:3B
        inet addr:207.101.236.21   Bcast:207.101.236.255  Mask:255.255.255.0
        inet6 :FE8O::202:b3ff:feOa:3736164 Scope: link
        UP BROADCAST RUNNING MULTICAST    MTU:1500 metric:1
        RX packets:7731 errors; 0 dropped:0 overruns:0 frame:0
        TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:1245192 (1.1MiB)  TX bytes:588 (588.0b)

lo      Link encap: Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr:   ::1/128   Scope Host
        UP LOOPBACK  RUNNING    MTU:16436 metric:1
        RX packets:990703 errors; 0 dropped:0 overruns:0 frame:0
        TX packets:990703 errors; 0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:77583230 (73.9 MiB)  TX bytes:77583230 (73.9 MiB)



grep dhclient resulted in nothing.  just went down one line with no prompt



results for cat /etc hosts:

127.o.o.1 localhost.localdomain   localhost  ubuntu

# the following lines are desirable for IPv6 capable hosts
:: 1  ip6-localhost  ip6-loopback
fe00::0 ip6-localhost
fe00::0 ip6-mcast prefix
fe00::1 ip6-allnodes
fe00::2 ip6-allroutes
fe00::3 ip6-allhosts


results for cat/etc/network/interfaces:

auto lo
iface lo inet loopback

mapping hotplug
            script grep
            map eth0


iface eth0 inet static
address 207.101.236.21
netmask 255.255.255.0

iface eth1 inet dhcp

auto eth0



When i installed debian it seemed to "figure it all out' on its own.  I will try to ping router

---

### Post by amohanty on 2005-12-14
> 127.o.o.1 localhost.localdomain localhost ubuntu


This is wrong. Its supposed to be 127.0.0.1 (zeros not o). Fix that in /etc/hosts
and try then do the following at the terminal

> sudo /etc/init.d/networking restart

I think its called networking. after you type netw just press the tab key and it will auto complete.

If it was a typo ignore the above. From the output the ip seems 207.101.236.21 seems to indicate that you are directly connected to the modem. Are you using the router as a dhcp server?

HTH

---

### Post by indeepthought on 2005-12-14
definitely a typo.  No, we are not using router as a DHCP server.  Forgive me being so green.  I'm trying to learn networking basics and linux at the same time.  i have a challenging year ahaed of me but i think it will be worth it.

---

### Post by amohanty on 2005-12-14
Ok then verify two things:

1. Your router recognizes 207.101.236.21 as a static IP. Look around in the router settings, disable dhcp server and make sure that the address is listed as a static passthrough IP.

2. That you have two (2) static IP addresses from your ISP, because your router is using one too (provided it is the box connected to the DSL/cable modem). 

HTH
AM

---

### Post by indeepthought on 2005-12-14
You may be on to something.  i will go verify these things.

---

### Post by indeepthought on 2005-12-14
I'm still trying to find this information.  I think i am looking at the wrong router.  thanks for your patience

---

### Post by indeepthought on 2005-12-15
I found a short term solution.  We have several static IP addresses available.  After rerouting some cables , i was able to connect by going the DHCP route.  This works as a short term fix to do what I need via internet (like downloading PHP etc) but will have to be abandoned.  I still can't figure out why it worked so easily with Debian

---

