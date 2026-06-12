---
title: "internet help"
date: 2006-01-04
forum: General Help
---

### Post by peedmar on 2006-01-04
it tells me that i'm not connected to the internet but when in fact i am. Anyone know who to fix this?

---

### Post by zoiks on 2006-01-04
My car keeps telling me a door is a jar, but in fact it's just a door.  More info needed.  ;)

---

### Post by peedmar on 2006-01-05
well my ethernet cord is in and everything and modem is working fine but when i try to use the web browser no sites work

---

### Post by professor_chaos on 2006-01-05
can you ping the same sites?
has your internet/browser worked before?
what kind of modem? Dialup, or dsl??

---

### Post by FizDev on 2006-01-05
if you do the command "ifconfig" do you see the eth0. If yes, does it says that you have an IP?
Also, are you connected directly to the modem or through a router?

---

### Post by peedmar on 2006-01-05
i just installed it today, i have a direct brodband connection


and where exactly do i do the command "ifconfig"

---

### Post by professor_chaos on 2006-01-05
try configuring your network with Applications -> System Tool -> Network Tools
sounds like you'll want to use DHCP, unless you IP gave you a fixed IP address

ohh, and you execute the "ifconfig" from the commandline or shell terminal. Applications -> Accesories -> Terminal

---

### Post by peedmar on 2006-01-05
i tried both those and didn't work, i "ifconfig" doesn't seem to work at all when i type it in

---

### Post by FizDev on 2006-01-05
Hmmm... you must type it without the quotes in the terminal.
```
ifconfig
```

It should give you something similar to this :
```

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:8E:76:54
          inet6 addr: fe80::2c0:9fff:fe8e:7654/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x5000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1730386 (1.6 MiB)  TX bytes:1730386 (1.6 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:AE:7B:C7
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:feae:7bc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18666579 (17.8 MiB)  TX bytes:1414439 (1.3 MiB)
          Memory:b0206000-b0207fff

```

But it my case I use the wireless (wlan0) instead of the ethernet (eth0). Post your results after if possible =)

---

### Post by peedmar on 2006-01-05
i did type it without the "

---

### Post by FizDev on 2006-01-05
...strange, when you execute the command
```
lspci
```
Do you see your Ethernet controller?

---

### Post by peedmar on 2006-01-05
nope it just said that the command wasn't right or something

---

### Post by FizDev on 2006-01-05
I really don't know, it looks like you're missing a lot of things. Maybe you should consider a fresh install. Sorry :(

---

