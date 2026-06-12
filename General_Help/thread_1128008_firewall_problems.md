---
title: "firewall problems"
date: 2009-04-17
forum: General Help
---

### Post by m@lvin superstar on 2009-04-17
Hi guys:D my name is Malvin from italy.. I'm so glad to be a part of this great community and it would be fantastic if somebody could help me.
Problem:
A few days ago i installed on my PC Ubuntu 8.10 and I'm glad abaut my choice because it works simply great but i still can't understand how to disable or change the firewall on my PC and which to install cause it gives me problem whith some programs such amule and makes it work slowly...
It's a pleasure to meet you all...
Waiting for your answer, thanks in advance.

---

### Post by TheLions on 2009-04-17
go to programs->Add/remove programs and install program called 'Firewall configuration'

---

### Post by brian_p on 2009-04-17
> **m@lvin superstar said:**
> 

Problem:
A few days ago i installed on my PC Ubuntu 8.10 and I'm glad abaut my choice because it works simply great but i still can't understand how to disable or change the firewall on my PC and which to install cause it gives me problem whith some programs such amule and makes it work slowly...


A firewall filters packets. A default Ubuntu install does no filtering. Here, this is on my machine:

```
brian@laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

So whatever your problem is it is not related to iptables. There is nothing to disable or change so programs like firestarter will do nothing for you.

---

### Post by uncle-c on 2009-04-17
You should enable UFW, Uncomplicated Firewall, which is basically a configuration tool for iptables. It comes as standard. Plenty of easy HOWTOS about.

[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

Should get you going.

---

### Post by mb_webguy on 2009-04-17
> **m@lvin superstar said:**
> Hi guys:D my name is Malvin from italy.. I'm so glad to be a part of this great community and it would be fantastic if somebody could help me.
Problem:
A few days ago i installed on my PC Ubuntu 8.10 and I'm glad abaut my choice because it works simply great but i still can't understand how to disable or change the firewall on my PC and which to install cause it gives me problem whith some programs such amule and makes it work slowly...
It's a pleasure to meet you all...
Waiting for your answer, thanks in advance.

As brian_p said, the firewall on a defaul Ubuntu installation does not block anything by default, so your problems are caused by the firewall.  More likely, you're behind a router and need to enable port forwarding on the router for those applications.

---

