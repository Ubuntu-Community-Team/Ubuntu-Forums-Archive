---
title: "Configuring Network Manager"
date: 2009-06-03
forum: General Help
---

### Post by theWrkncacnter on 2009-06-03
Hey is it possible to get network manager to do the same thing as
```
sudo ifconfig eth0 192.168.0.1
sudo ifconfig eth0 up
```

If I do it manually, I get my nice manual ethernet connection between my ubuntu computer and my macbook, but I have to disable network manager to do it. I'd like nm to configure both networks so I can access both at the same time.

Thanks!

---

### Post by blueridgedog on 2009-06-03
You can click "add" in network manager and add another ip to a given interface (you can name it Mac if that helps keep it straight).  I assume when you say "both" you are indicating that there is another network that the Ubuntu system is connecting too?

---

### Post by theWrkncacnter on 2009-06-03
Yes -- There is one wireless lan all the computers in my home connect to, with IP addresses like 192.168.1.x
I use the secondary network to take advantage of ethernet's faster transfer speeds.
I added an ethernet interface called "Mac," and gave it the IP 192.168.0.2 and a subnet of 255.255.0.0. Network manager connects to it, and the mac reports that ethernet is connected, but they can't ping each other, so something is not the same as how it was when I did it manually.

Is the subnet mask wrong? I'm still not sure how those work.

---

### Post by blueridgedog on 2009-06-03
What is the IP address and mask used on the Mac?

---

