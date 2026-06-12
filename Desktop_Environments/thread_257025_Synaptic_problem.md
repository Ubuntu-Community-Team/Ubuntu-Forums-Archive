---
title: "Synaptic problem"
date: 2006-09-13
forum: Desktop Environments
---

### Post by waltervalderrama on 2006-09-13
Hi, please i need help. Synaptic crashes when i want to launch it. After typing synaptic, i get the following error::

andre@valderrama:~/dyndns/ez-ipupdate-3.0.11b7$ sudo synaptic
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory


It seems like there is a library or something missing..... I dont know, please help!!!!!!!!!!!

---

### Post by meng on 2006-09-13
Quite a few folks have had this problem. Search the forums for libvte.so.4 and you should find your answer.

---

### Post by bruenig on 2006-09-13
meng is correct also, gksudo synaptic is preferred over sudo synaptic

---

