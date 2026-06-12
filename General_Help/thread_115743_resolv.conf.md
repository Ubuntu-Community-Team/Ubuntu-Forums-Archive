---
title: "resolv.conf"
date: 2006-01-11
forum: General Help
---

### Post by myha on 2006-01-11
Hi all!

I am having problems with my resolv.conf file...
On work I use eth0 connection, but when I come homw I have wireless connection... And every time that I switch networks my resolv.conf file gets messed up and I have to manually rewrite it and restart networking for things to work...

How can I change that? It is really annoying....  :/

---

### Post by milstead on 2006-01-11
resolv.conf can get changed by the DHCP client. The DHCP client is what automatically works out your IP address and nameservers when you connect to each network. This is instead of using a static IP address. One solution is to make everything static (not use DHCP) and include both your work and home nameservers in resolv.conf. The problem is that this will slow down name look ups. The alternative is to create a new location for home and work in the network settings dialog. I assume this allows you to have more than set of nameservers or DHCP settings.

Timie Milie

---

### Post by myha on 2006-01-12
Hello Milstead,

thanky you for the reply. It seems logical that DHCP rewrites resolv.conf file, I dont know why I didnt think of it before. I will try this as soon as I come home today!

Best regards,
Miha

---

