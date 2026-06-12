---
title: "acess server inside network"
date: 2009-04-17
forum: General Help
---

### Post by dapim on 2009-04-17
how can i acess server 10.0.0.2  this server is inside a network at my home with ip xx.xx.xx.xx

but i want acess this server from my job, how can i do it?
because adress 10.0.0.2 doesn't go to server at home ahen i try to acess it

---

### Post by shel-hall on 2009-04-17
> **dapim said:**
> how can i acess server 10.0.0.2  this server is inside a network at my home with ip xx.xx.xx.xx

but i want acess this server from my job, how can i do it?
because adress 10.0.0.2 doesn't go to server at home ahen i try to acess it
Addresses in the 10.x.x.x group aren't routable.  Logical, if you think about it; how would the Internet know you meant your 10.x.x.x machine instead of mine?

To route incoming connections from the Internet to a machine on your LAN, you have to set it up in your router.  This is usually called "port forwarding" but does have other names.  Once this is done, the IP address of the Internet "side" of your router becomes the public IP address of your machine for the ports you forward.

-Shel

---

