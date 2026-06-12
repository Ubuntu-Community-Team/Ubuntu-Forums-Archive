---
title: "Exposing SSH to the outside world?"
date: 2009-06-05
forum: General Help
---

### Post by Vunutus on 2009-06-05
So far I've primarily been using SSH to connect to my desktop from a local (wireless) network via my laptop. In a few hours I have to go somewhere and there's a very good chance I will need to SSH my home machine to do some operations. On my home machine I have a dynamic DNS thing from noip.com that gives me a DNS address like myname.noip.com. Whenever I try to connect via SSH using this address, it just hangs. This leads me to believe that my SSH server is not being exposed to the world past my router. 

My first guess would be that I need to set up port forwarding on my router. A quick google search told me that SSH uses port 22 by default. Will forwarding this port to my home machine cause SSH to work? Normally I'd just try something like this without asking but I know port 22 isn't exclusive to SSH so could this cause a security risk?

---

### Post by Celauran on 2009-06-05
Port 22 is the default SSH port, but you can easily modify your sshd_config so that it uses a different port. For more security, disable password logins and only allow logins via RSA key.

---

### Post by blueridgedog on 2009-06-05
Simply moving the port will not make it more or less secure.  Think of the old IT saying, security through obscurity is no security.  The port will still be exposed in a scan and the same scan will reveal that it is probably an ssh server.  You can (as the other poster mentioned) use keys only, or simply make and keep great passwords.  The world runs on ssh managed systems.  You can restrict the IP addresses that you allow to connect to your systems (a common tactic) via iptables or hosts.allow.

---

### Post by Vunutus on 2009-06-05
Alright I'm still having some problems. Since I just need this to work for about 3 hours, I've opted to create a security hole for myself by forwarding port 22 to my home machine and enabling password authentication.

I did this, but it didn't work. I set up my router to forward port 22, but whenever I try to SSH my machine through my public IP address or domain name, it just hangs. If I do "ssh localhost" or any other "internal" name, it works fine, however. I'm fairly certain I did the port forwarding correctly since I have several other things forwarded which DO work correctly.

---

### Post by Vunutus on 2009-06-05
OK it seems to have changed a bit

Instead of just hanging now it says "connection refused". I've checked iptables as well as my router's firewall and neither of them appear to be blocking port 22.

---

### Post by Celauran on 2009-06-05
Nevermind.

---

### Post by Vunutus on 2009-06-05
Another update:

It appears it's not just SSH that will not work from the outside world. The MySQL server I had set up is not accessible from anywhere but my internal network either.

I don't understand why, I have them both forwarded on the correct ports and I did it the exact same way I did several other port forwards (that are unquestionably working).

---

### Post by fang0654 on 2009-06-05
For SSH, look and see if you can find anything in the log file /var/log/auth.log which might give you a clue as to why you are being rejected.  

For mysql, comment out the following line in /etc/mysql/my.cnf

```
bind-address = 127.0.0.1
```

becomes

```
# bind-address = 127.0.0.1
```

---

### Post by MikeTheC on 2009-06-05
Is it possible your ISP is simply blocking your machine?

Also, how do you have your router configured exactly?

---

### Post by blueridgedog on 2009-06-05
If you can ssh from one system on your LAN to the system in question, using its internal IP address, then the ssh part is working.  What remains is the router, your ISP policy, your local machine firewall and hosts allow/deny.

Though it may be a bit of complex process, I would use tcpdump to dump packets on the box while attempting to ssh from an outside host to the box in question.  That should get you to the next step in trouble shooting.

---

### Post by MikeTheC on 2009-06-05
No matter what you can do on your own local network, in order for you to do anything in the outside world with devices on your local network, at a MINIMUM your router must be set up to route certain kinds of traffic (typically based on port number) to a given machine on that network.

Also make sure that you're using a router-assigned IP address to the computer in question. This allows for centralized control of network IP addresses and is generally a superior approach to the old-school trick of doing manually-assigned static IPs.

---

### Post by Vunutus on 2009-06-05
> **fang0654 said:**
> For SSH, look and see if you can find anything in the log file /var/log/auth.log which might give you a clue as to why you are being rejected.  

For mysql, comment out the following line in /etc/mysql/my.cnf

```
bind-address = 127.0.0.1
```

becomes

```
# bind-address = 127.0.0.1
```

Did that already, MySQL is in the same boat as SSH though, machines in my local network can connect but nothing else can.

> **MikeTheC said:**
> Is it possible your ISP is simply blocking your machine?

Also, how do you have your router configured exactly?

It's possible that my ISP is blocking it but I really really doubt it. I haven't had them do anything like this so far and they seem to be rather unintrusive as far as ISPs go.

> **blueridgedog said:**
> If you can ssh from one system on your LAN to the system in question, using its internal IP address, then the ssh part is working.  What remains is the router, your ISP policy, your local machine firewall and hosts allow/deny.

Though it may be a bit of complex process, I would use tcpdump to dump packets on the box while attempting to ssh from an outside host to the box in question.  That should get you to the next step in trouble shooting.

I'm pretty sure firewalls aren't at fault here. I run "iptables -L" and it does not return anything other than the default configuration, mentioning nothing about the ports in question. I've tried disabling my router's firewall and that didn't change anything, and nothing shows up in firewall logs related to these ports.

Hunting through packets isn't something I know how to do, but it is on my list of "things to learn sometime". Looks like now's a good time to start :p

---

### Post by blueridgedog on 2009-06-06
> **Vunutus said:**
> 

Hunting through packets isn't something I know how to do, but it is on my list of "things to learn sometime". Looks like now's a good time to start :p

At this point you are stuck unless you verify the connection is getting to your internal system.  You will need to ssh to a remote system, then attempt to ssh back to your public IP which has been forwarded to your Ubuntu system and run tcpdump in a window looking for incoming packets.  You will need to specify the tcpdump command such that you do not see your other ssh session if you are using that host as the host to initiate the test on.

look at the man page for tcp dump, but here is an example that I would start with:
```

 sudo tcpdump dst host 192.168.1.100 and dst port 22
```

This dumps packets that are to my private address and to port 22.  If I ssh to my system from another one, it starts.

```
08:08:01.233420 IP tori.local.51001 > Ripstop.local.ssh: . ack 1744 win 165 <nop,nop,timestamp 4294908178 16860839>
08:08:01.292296 IP tori.local.51001 > Ripstop.local.ssh: P 1063:1127(64) ack 1744 win 165 <nop,nop,timestamp 4294908193 16860839>
08:08:01.340379 IP tori.local.51001 > Ripstop.local.ssh: . ack 1808 win 165 <nop,nop,timestamp 4294908205 16860865>
```

Or, if I turn off name lookups:

```

 sudo tcpdump -n dst host 192.168.1.100 and dst port 22
```

```
08:10:11.504611 IP 192.168.1.102.51002 > 192.168.1.100.22: P 1015:1063(48) ack 1696 win 165 <nop,nop,timestamp 4294940745 16893407>
08:10:11.546605 IP 192.168.1.102.51002 > 192.168.1.100.22: P 1063:1127(64) ack 1744 win 165 <nop,nop,timestamp 4294940756 16893407>
08:10:11.633091 IP 192.168.1.102.51002 > 192.168.1.100.22: . ack 1808 win 165 <nop,nop,timestamp 4294940778 16893429>
```

---

