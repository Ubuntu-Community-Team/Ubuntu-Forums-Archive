---
title: "Share eth1 over eth0"
date: 2005-08-26
forum: Desktop Environments
---

### Post by daller on 2005-08-26
Hi All,

I have 2 computers, one with wireless, and one without!

How do I enable the first computer to share its wireless connection with the other computer?

wireless: eth1
wired: eth0

Please help!

---

### Post by ::DoGG:: on 2005-08-26
Assuming You are running kernel 2.6 You already have iptables builtin kernel so type in console:
```

iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT


# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i ! eth1 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow outgoing connections from the LAN side.
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT

# Masquerade.
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

# Don't forward from the outside to the inside.
iptables -A FORWARD -i eth1 -o eth1 -j REJECT

# Enable routing.
echo 1 > /proc/sys/net/ipv4/ip_forward

``` 


And above should be done on wireless machine
( i assume that both of them are linux)

Then all you have to do is on the "machine without the internet" set the default gateway to the router machine interface eth0 ( on aove rule i assumed that eth1 is you EXTERNALL interface" remember about makin a good adresses and masks and broadcasts).

That should do the trick.

---

### Post by daller on 2005-08-26
Well, I created a shellscript with the commands!

About the gateway address, I have no ip on eth0 on the connected pc: (the one with wireless)

root@dallap:/home/daniel # ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0D:56:33:1E:CB
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:04:23:83:68:80
          inet addr:192.168.0.2  Bcast:192.168.63.255  Mask:255.255.192.0
          inet6 addr: fe80::204:23ff:fe83:6880/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1985066 errors:367 dropped:0 overruns:0 frame:0
          TX packets:2074770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2911398301 (2.7 GiB)  TX bytes:128621260 (122.6 MiB)
          Interrupt:5 Base address:0x8000 Memory:faffc000-faffcfff


How is this accomplished?

If possible, I would like to have it integrated into the shellscript!

---

### Post by drummer on 2005-08-26
Hi, I want to do this also, can I use my computer connected wirelessly to route the net connection to a lan switch or router? and then have multiple wired computers connected to the switch? what is a gateway exactly (IP?) and what should i set the wired computers up with in this case?

---

