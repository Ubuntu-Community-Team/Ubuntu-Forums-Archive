---
title: "Can't browse the internet when connected to local network"
date: 2009-04-30
forum: General Help
---

### Post by perrti-y02 on 2009-04-30
Hello,

I have already posted this on the Wireless and Networking forum but had no response.

Whenever I connect to my own network (used for file server and general tinkering, IP is 192.168.2.x?!) I am unable to browse the internet which comes in on my Wifi card (IP 192.168.1.101). If I am not connected to the wired network then I can happily browse the interweb.

Any ideas what my problem is? I think it is trying to find the interweb on my local network, where it clearly isn't.

I am running 9.04 and everything is using static IP addresses.

---

### Post by dcstar on 2009-04-30
> **perrti-y02 said:**
> Hello,

I have already posted this on the Wireless and Networking forum but had no response.

Whenever I connect to my own network (used for file server and general tinkering, IP is 192.168.2.x?!) I am unable to browse the internet which comes in on my Wifi card (IP 192.168.1.101). If I am not connected to the wired network then I can happily browse the interweb.

Any ideas what my problem is? I think it is trying to find the interweb on my local network, where it clearly isn't.

I am running 9.04 and everything is using static IP addresses.

You may have to change the default/Gateway route:

```
netstat -rn
```

---

### Post by perrti-y02 on 2009-05-01
The output from netstat are as follows. The first one is without the wired connection second is with the wired connection.

tim@shuttle:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
tim@shuttle:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.100   0.0.0.0         255.255.255.255 UH        0 0          0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.100   0.0.0.0         UG        0 0          0 eth0

Can anyone translate?

---

### Post by markthecarp on 2009-05-01
> **perrti-y02 said:**
> The output from netstat are as follows. The first one is without the wired connection second is with the wired connection.

tim@shuttle:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
tim@shuttle:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.100   0.0.0.0         255.255.255.255 UH        0 0          0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.100   0.0.0.0         UG        0 0          0 eth0

Can anyone translate?

The wired connection is looking at 192.168.1.100 as it's gateway. The wireless is looking at 192.168.1.1 for it's gateway. Change the settings for eth0 to use 192.168.1.1 as it's gateway. I'd also recommend using the same set of addresses for both wired and wireless (192.168.1.x or 192.168.2.x) mixing the addresses can cause routing headaches that aren't worth it for a home LAN.

KISS is a good principle to follow.

-mark

---

### Post by perrti-y02 on 2009-05-01
The logic for that is because 192.168.2.x is on the ethernet card it is then looking for my wireless card which has the address 192.168.1.100. the ethernet card is subsequently looking for the wireless router at 192.168.1.1

I might be misunderstanding this but I didn't thik that IP 192.168.2.10x could use 192.168.1.1 as its gateway. I will give it a go and see what happens.

---

### Post by perrti-y02 on 2009-05-01
Changing that default route doesn't help. Same problem is there and netstat looks as follows.

tim@shuttle:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.1     0.0.0.0         255.255.255.255 UH        0 0          0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

Any more ideas? I notice that when only on Wireless there are 2 entries for wlan0 but when on wireless there is only one. Is this significant?

---

### Post by perrti-y02 on 2009-05-01
I have found a solution but I don't really know what I have done. There was a box saying "use this connection only for resources on its network" which makes it never be the default network. It now works but I'm not sure what it has actually done.

Anyone know?

---

