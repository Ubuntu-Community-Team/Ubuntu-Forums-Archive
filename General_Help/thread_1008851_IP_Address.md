---
title: "IP Address"
date: 2008-12-11
forum: General Help
---

### Post by speakerguru on 2008-12-11
Can anyone tell me if it is possible to change from DHCP to a permanent ip address on my networked ubuntu machine without using the shell?
Can it be done easily and if so can someone explain in detail on how to do it?
Thanks any help for this beginner is appreciated.:popcorn:
I want to give my machine a specific ip address.

---

### Post by lisati on 2008-12-11
If the IP is assigned by your ISP that's something you'll have to take it up with them as part of the process of setting things up. If, however, it's the IP address on your local network, it's usually easy enough to set a specific IP address for a particular machine on most modern routers.

On the occasions I've set a static address on my router for specific machine(s), Ubuntu has been happy to use the provided address without the need to turn off DHCP. The only time I've encountered a problem is when the changes I've made on the router affect more than one machine, it's easily fixed, often by restarting networking.

---

### Post by MedianMajik on 2008-12-11
> **speakerguru said:**
> Can anyone tell me if it is possible to change from DHCP to a permanent ip address on my networked ubuntu machine without using the shell?
Can it be done easily and if so can someone explain in detail on how to do it?
Thanks any help for this beginner is appreciated.:popcorn:
I want to give my machine a specific ip address.

Welcome to the forum!  You'll need to use the shell to set a static IP address.  Thankfully, you can cut and paste the directions from someone on the forum more knowledgeable on the topic than I.
  Don't Panic!  This handy [guide]("http://gd.tuwien.ac.at/.vhost/linuxcommand.org/learning_the_shell.php") makes a good introduction to the Linux shell.

---

### Post by speakerguru on 2008-12-12
I am sorry but did not make myself clear. I have a home network with macs and pc's tied together. I have a permanent IP address supplied by my ISP but I want to give my Linux machine a dedicated IP address. I can not find a way to do it as it sets up automatically with a dhcp address dished out by the router.
It is simple to set one up in windows by clicking properties on the network icon but not in ubuntu


> **lisati said:**
> If the IP is assigned by your ISP that's something you'll have to take it up with them as part of the process of setting things up. If, however, it's the IP address on your local network, it's usually easy enough to set a specific IP address for a particular machine on most modern routers.

On the occasions I've set a static address on my router for specific machine(s), Ubuntu has been happy to use the provided address without the need to turn off DHCP. The only time I've encountered a problem is when the changes I've made on the router affect more than one machine, it's easily fixed, often by restarting networking.

---

### Post by bab1 on 2008-12-12
The default GUI interface for IP configuration is Network Manager.  A good article on the subject can be found [[COLOR="DarkGreen"]**here**[/COLOR]]("http://www.arachnoid.com/linux/NetworkManager/index.html")[COLOR="Green"]****[/COLOR]

---

