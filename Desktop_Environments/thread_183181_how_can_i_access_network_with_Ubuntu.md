---
title: "how can i access network with Ubuntu?"
date: 2006-05-27
forum: Desktop Environments
---

### Post by ec2 on 2006-05-27
i have adsl connection. It works with winxp, but Ubuntu doesn't recognioze it.

i have password access to internet, and i don't know where to enter the password and username.

---

### Post by waffen on 2006-05-27
Go to: System>Administration>Network

---

### Post by jvictor on 2006-05-28
First there are couple of things you need to tell us 

1) Are u connecting thru a router ?
2) Do u use a network cable - network card or is it some other means

Assuming that you use a router , u can use a static IP and manually set up the DNS server information where waffen said. U amy also need to disable IPV6 

There are **NUMEROUS* threads inthe is forum on how to do it.

If not a network card , then connect the machine using USB / wt ever thingy which ur ISP has given and run 

$sudo pppoeconf

---

### Post by ec2 on 2006-05-31
actually, i only need to find the place to insert the username and password, but i can't find it. Is there a network connections place in Ubuntu, like in Windows?

---

### Post by jvictor on 2006-06-03
looks like u need to run ppoeconf

---

