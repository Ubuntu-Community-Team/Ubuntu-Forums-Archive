---
title: "Strange Wireless Problem"
date: 2005-12-18
forum: General Help
---

### Post by Baloo on 2005-12-18
I've just installed Ubuntu on my Acer Aspire 3003 Laptop with a Netgear WG511T wireless lan card which uses the Atheros chipset. Now I thought this was supposed to work 'out of the box' but I have the strange problem where I can connect to my routers setup page, browse my internal windows network and even stream music wirelessly but I cannot connect to any external web site. 

Anyone have any clues on what to check next, I'm really lost on this one.

---

### Post by Lambert on 2005-12-18
1. post the output of this command 

route

2. try to ping ip then common name

ping -c 4 82.211.81.130

ping -c 4 [www.ubuntulinux.com](www.ubuntulinux.com)

What's the results?

---

### Post by rcerreto on 2005-12-18
Well, if you can access your wireless router that means that your wireless card is working fine.
Some network setting must be wrong.

Three things are to be set:
1)  IP Address
2)  DNS Address(es)
3)  Default Gateway

When you get config via DHCP (any router will usually act as a DHCP server) it's very likely that the three parameters are OK.

If you're setting your IP Address by hand, you'll have to remember to set other parameters too.

To know your currently active DNS:
**cat /etc/resolv.conf**

To verify whether routing is working properly:
**route**

Hope that helps, if not try posting the output of mentioned commands.

---

### Post by Baloo on 2005-12-19
Ok, this seems like a DNS problem now.

Output of various commands

**iwconfig**

```

ath0      IEEE 802.11g  ESSID:"SWAMR-54108"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:30:54:40:8A:42   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/94  Signal level=-56 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

**/etc/resolv.conf**
```

search 192.168.1.1
nameserver 192.168.1.1

```

**route**
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 ath0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 ath0

```

but most interesting of all the ping to ubuntulinux doesn't work but using the ip address of ubuntulinux does work.

Any idea's?

---

### Post by rcerreto on 2005-12-19
That makes sense, if you can't get DNS services you can't resolve a symbolic address ([www.ubuntu.com](www.ubuntu.com)) into its IP address (82.211.81.130).
But you *have* internet access so you can access IP addresses.

Your settings try to use your wireless router as a DNS server but that's clearly not working.

You need to edit /etc/resolv.conf  

it has to look like:

nameserver  xxx.xxx.xxx.xxx

where xxx.xxx.xxx.xxx is your ISP DNS IP address

if you don't know its value but you have some other box on your network which can access the internet, you can get the correct value from there.
On a windows box, open a DOS command prompt and type:

ipconfig /all

look at the output and you'll find the DNS address. Put it into /etc/resolv.conf and that's all.

---

### Post by Baloo on 2005-12-19
Thanks for all the help.

After alot of digging on google I found out that my router has DNS problems. Putting my isp's DNS servers in manually in the network settings program solved my problem and I'm now posting from Linux :)

---

