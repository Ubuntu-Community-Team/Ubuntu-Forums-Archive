---
title: "IP Addressing."
date: 2008-12-26
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2008-12-26
im trying to find out my lan IP address on Ubuntu.

i have tried ifconfig and for my adapter it gives me a 10.x.x.x address. the mask is also 255.255.255.0  i dont understand this to be honest as my gateway is 192.168.1.x with a mask of 255.255.255.0.

how is that even possible? is there something i am missing?

---

### Post by northern lights on 2008-12-26
```
sudo lshw -C network
```will display only one IP if the rest confuses you.

Alternatively you could post your *ifconfig* (Check *inet addr*).

---

### Post by NiGhtMarEs0nWax on 2009-01-21
ok sorry for the late reply :) turns out 10.x.x.x is reserved for special addressing, mainly because my installation is being run inside a virtualbox VM, i guess i should have mentioned that. what i needed was to forward ports for ubuntu to make use of, which is done on the host OS. i have solved this issue thanks.

---

