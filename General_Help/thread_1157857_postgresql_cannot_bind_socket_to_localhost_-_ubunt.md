---
title: "postgresql cannot bind socket to localhost - ubuntu 8.10"
date: 2009-05-13
forum: General Help
---

### Post by pkcpkc on 2009-05-13
Hi, 

I installed postgresql on ubuntu 8.10 via aptitude install. 

the installation ran fine, except for the dpkg --configure that showed an issue so the daemon didn't start. 

I ran an strace against the process, and it showed that the process cannot bind the required port on localhost / 127.0.0.1. 

this is the same if I try to change the port number. 

Is there a way to knwo what blocks the socket binding attempt ?

---

