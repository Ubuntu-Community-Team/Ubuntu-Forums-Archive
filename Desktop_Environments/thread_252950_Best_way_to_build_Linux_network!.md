---
title: "Best way to build Linux network?!"
date: 2006-09-07
forum: Desktop Environments
---

### Post by oocce on 2006-09-07
Hi!
I'm using Ubuntu on my Desktop and Kubuntu (for a change) on my laptop. What is best way share files and folders between them? Is samba meant to Linux-Windows combinations only? I had conf samba and it's not working "like a charm". 
I would like to have permissions each others to read and write (propably with groups?). BUT I dont want change permissions to 777, because of WLAN!

I just want things work, without any ftp shit =). I Don't understand this "group"-thing.

Anybody have a minute or two to help me out..

Thanks for all answering!

---

### Post by jimbren on 2006-09-07
I'd recommend using NFS in order to share folders.  It's pretty easy to set up.

Here's a howto:
[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html)

---

### Post by oocce on 2006-09-07
> **jimbren said:**
> I'd recommend using NFS in order to share folders.  It's pretty easy to set up.

Here's a howto:
[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html)

I must to try this! Thanks! Hopefully it is not too complicated :| There should be easy way to control network..

---

### Post by Herman on 2006-09-07
Hello, oocce,
SSH works well too for a local area network, and is very simple to set up. (Almost) no knowledge is necessary! :D
Here's a link for how I set mine up, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")
Regards, Herman :D

---

### Post by jimbren on 2006-09-08
It's not too bad.  Let me know how it goes...

---

### Post by oocce on 2006-09-08
> **Herman said:**
> Hello, oocce,
SSH works well too for a local area network, and is very simple to set up. (Almost) no knowledge is necessary! :D
Here's a link for how I set mine up, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")
Regards, Herman :D

Thanks! This sounds perfect, expect that my internet-operator demand DHCP... :|

I must give up with NFS too? Static ip-address is needed with both styles?

---

### Post by Herman on 2006-09-08
>  Thanks! This sounds perfect, expect that my internet-operator demand DHCP... :neutral:
I must give up with NFS too? Static ip-address is needed with both styles?       oocce, that depends, obviously, on your ISP. With my ISP, Telstra Bigpond Australia, I can phone them or contact them on the internet and arrange for a static IP address, but it will cost me an extra $10 per month and will not be as secure as a 'roving' IP address.
However, by using a router, which costs about $125 to $175 or so, the router handles the 'roving' IP address for the outside world (the internet), and allows me to use 'static IP addresses for inside my LAN.
Also, the router comes with an excellent 'hardware firewall', which is an added bonus which is well worth considering. Most routers have one.
So the router is not only more cost effective, it also gives me far better security. My router was very easy to set up too, all I had to do was plug it in and it worked automatically right away. One wire for power, one cable plugged into the ADSL broadband internet modem, and a cable to each computer's ethernet port.

If you can't afford or don't want to spend any money, then it would be possible to use a cat5 crossover cable or two cat5 cables and a hub to connect your two computers, but I agree with you, it would be a nuisance to need to keep swiching from static IP to DHCP all the time every time you want to use the internet.

Consider investing in a router maybe? :D

Regards, Herman

---

### Post by oocce on 2006-09-09
> **Herman said:**
> oocce, that depends, obviously, on your ISP. With my ISP, Telstra Bigpond Australia, I can phone them or contact them on the internet and arrange for a static IP address, but it will cost me an extra $10 per month and will not be as secure as a 'roving' IP address.
However, by using a router, which costs about $125 to $175 or so, the router handles the 'roving' IP address for the outside world (the internet), and allows me to use 'static IP addresses for inside my LAN.
Also, the router comes with an excellent 'hardware firewall', which is an added bonus which is well worth considering. Most routers have one.
So the router is not only more cost effective, it also gives me far better security. My router was very easy to set up too, all I had to do was plug it in and it worked automatically right away. One wire for power, one cable plugged into the ADSL broadband internet modem, and a cable to each computer's ethernet port.

If you can't afford or don't want to spend any money, then it would be possible to use a cat5 crossover cable or two cat5 cables and a hub to connect your two computers, but I agree with you, it would be a nuisance to need to keep swiching from static IP to DHCP all the time every time you want to use the internet.

Consider investing in a router maybe? :D

Regards, Herman
Hi! I have this [http://en.wikipedia.org/wiki/WRT54G](http://en.wikipedia.org/wiki/WRT54G). But I dont have a clue what should I do, this NAT-thing is making me confused =)

---

