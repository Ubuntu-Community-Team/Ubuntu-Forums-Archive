---
title: "Network problems"
date: 2005-10-17
forum: Desktop Environments
---

### Post by CyberDon on 2005-10-17
Hi all,

I installed Ubuntu 5.10 and it worked for two days, last night my network syoped working. It cannot rosolve naything. 

When Ubuntu boots up the network starts but it cannot synchronize the clock and afterwords I know that I will not be able to connect to the network.

What should I do, please anyone?

Douglas

---

### Post by Dr. Nick on 2005-10-17
Wired or Wireless? Check under "System - Administration - Networking" for any mention of it and post back with that and a model number and I may be able to help

---

### Post by CyberDon on 2005-10-21
It is wired network, running DHCP.

It seems that the DNS cannot be resolved, I had the same error eith Ubuntu 5.04.

Can someone tell me what to do?

---

### Post by LorenzoD on 2005-10-21
If the problem is related to DNS, check the file /etc/resolv.conf. You should find one or more lines labeled 
```
nameserver <ip address>
```

You need to make sure you are able to contact those DNS servers. Try pinging them. If you're not able to reach the name servers you probably have a routing problem.

If you don't have any nameserver entries, then you need to add them. If you have 127.0.0.1 as an entry in resolv.conf that means that your machine is responsible for resolving host names. That may indicate that you have NetworkManager running, but not necessarily.

---

### Post by Gordonbp531 on 2005-10-21
You can't add ip addresses directly to resolve.conf - it won't stick as it will be overwritten each bootup. You need to edit /etc/dhc3(?- I'm not at my Ubuntu machine right now)/dhclient.conf and unremark the line that begins #prepend....and replace 127.0.0.1 with your ISPs dns there.

HTH

---

