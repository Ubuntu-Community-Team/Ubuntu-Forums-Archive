---
title: "how can i transmit and recieve throw closed port in ubuntu 6.0"
date: 2009-06-18
forum: General Help
---

### Post by almofti on 2009-06-18
I am new in using ubuuntu and iam using it for a video conference solution as aclient pc iam traying to transmit o recieve but always there either **ICMP as 22222 port un reachaple** or no reult in the jmf application iam usint
 
**[COLOR=red]please time is shine ineed that so fast [/COLOR]**
 
with so gracful

---

### Post by Soul-Sing on 2009-06-18
which version of ubuntu are you "running"? 6.0.6 Dapper?

---

### Post by 3rdalbum on 2009-06-18
You cannot recieve through a closed port. You can transmit, but not recieve. This is the whole point of a firewall.

If you want to recieve the incoming connection, you must find out how to access the firewall in your router, and tell it to forward UDP port 22222 to your computer's IP address.

---

