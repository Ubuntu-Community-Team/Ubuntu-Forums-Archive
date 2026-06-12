---
title: "Internet issues"
date: 2009-03-18
forum: General Help
---

### Post by horax on 2009-03-18
I just installed Ubuntu on my friend's computer.

Install was flawless.  Updated all packages, libraries, etc.
Tested the internet connection on my local network, and it worked fine.

Dude took it home, plugged it into his network, and he cannot access any page in Firefox or any other browser.

Error says, "server not found."

Are there internet settings somewhere or something he can do to identify his PC with his own network?  Wondering if connecting to mine initially screwed up some automatic detection of the network or something.

hx

---

### Post by iaculallad on 2009-03-18
Had you configured your friends IP as static when you set it up? Maybe, you're friends is using dynamic IP that he can't renew it from DHCP. Ask him if he gets a reply when pinging his gateway IP address.

---

### Post by horax on 2009-03-18
How would he find his gateway address?

---

### Post by iaculallad on 2009-03-18
Issue the command below on your terminal:

```
netstat -rn
```

Gateway IP address should be under the Gateway column.

---

### Post by horax on 2009-03-18
Ok...I'll have him do this and I'll update the thread.

---

### Post by horax on 2009-03-19
So what should I do if he cannot ping his own system?

I tried it on my box and it worked just fine.

-hx

---

### Post by horax on 2009-03-19
Ok, my friend just did the netstat -rn, and there are NO IP addresses under Gateways or Destination.

HOw can we populate those correctly?

-hx

---

### Post by iaculallad on 2009-03-19
Could you post whatever outputs when you issue the command below:

```
ifconfig eth0
```

---

### Post by horax on 2009-03-19
I just got him hooked up with a static IP address....but let me see.

---

### Post by horax on 2009-03-19
eth0      Link encap:Ethernet  HWaddr 00:10:c:46:80:e0  
          inet6 addr: fe80::210:dcff:fe46:80e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:159649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10178734 (10.1 MB)  TX bytes:10044 (10.0 KB)
          Interpret:22 Base address: 0xe000

---

### Post by horax on 2009-03-19
Anybody else have any ideas on this?

---

### Post by horax on 2009-03-22
Gee, thanks for the follow up, guys.

---

