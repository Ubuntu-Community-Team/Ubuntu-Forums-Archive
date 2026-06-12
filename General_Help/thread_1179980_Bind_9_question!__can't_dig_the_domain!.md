---
title: "Bind 9 question! : can't dig the domain!"
date: 2009-06-06
forum: General Help
---

### Post by AlexenderReez on 2009-06-06
```
root@ubuntu:~# nslookup ns.radzi.com.hosts
Server:		168.118.218.185
Address:	168.118.218.185#53

** server can't find ns.radzi.com.hosts: NXDOMAIN

root@ubuntu:~# sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                 [ OK ] 
 * Starting domain name service... bind9                                 [ OK ] 
root@ubuntu:~# nslookup ns.radzi.com
Server:		168.118.218.185
Address:	168.118.218.185#53

** server can't find ns.radzi.com: NXDOMAIN


```

i think i have already configure radzi.com perfectly...so please detect my careless ...

---

