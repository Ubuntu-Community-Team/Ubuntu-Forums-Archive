---
title: "feisty fawn herd 3 network manager"
date: 2007-02-02
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-02-02
Network manager icon on top line says "no connection" as I make this entry.
The evidence is the  CDLive got out on the LAN, got the gateway address, and the DSL nameserver address, then after that feisty decided there was no connection.

From terminal session, ifconfig printout did not return an inet address, and in fact Firefox couldn't access the intenet.

Then I did "sudo dhclient" (from Official Ubuntu manual p. 211), now ifconfig returns an inet address, and Firefox got ubuntu.com so I could make this report.  The network manager icon still says "no connction".

I tried removing network manager with Synaptic but the icon is still there and still says "no connection".

---

### Post by pochu on 2007-02-03
Hi jerrylamos

Could you report this on [Launchpad]("https://launchpad.net/ubuntu/+filebug")?

Thanks
Pochu

---

### Post by kanenas on 2007-02-03
> **jerrylamos said:**
> Network manager icon on top line says "no connection" as I make this entry.
The evidence is the  CDLive got out on the LAN, got the gateway address, and the DSL nameserver address, then after that feisty decided there was no connection.

From terminal session, ifconfig printout did not return an inet address, and in fact Firefox couldn't access the intenet.

Then I did "sudo dhclient" (from Official Ubuntu manual p. 211), now ifconfig returns an inet address, and Firefox got ubuntu.com so I could make this report.  The network manager icon still says "no connction".

I tried removing network manager with Synaptic but the icon is still there and still says "no connection".

the same think happens on my test pc which is p3 1ghz, 440bx chipset, with intel 10/100 management adaptor

edit: by searching the launchpad I found bug 80622 as the author says 

sudo gedit /etc/network/interfaces and add "static" after "iface eth0 inet static" solves the problem, eventhough network manager still says no network I can surf using firefox, and leech,seed using ktorrent

---

### Post by jerrylamos on 2007-02-03
O.K., submitted bug #83143.

I might add I tried removing network manager with "Add/Remove" which then also marked Ubuntu Desktop for removal (!) which is why I tried to use Synaptic instead.  Sure would like to be able to remove a package with bugs.

---

### Post by pochu on 2007-02-03
There is no big problem in removing ubuntu-desktop: it's a meta package, so you won't remove nothing essential. However, when ubuntu-desktop is updated, you will lose the new dependencies it has, so I don't recommend removing it.

What you should do, instead of removing network-manager, is wait for a fix, and if it stops your work, try to disable it. However, you shouldn't work in Feisty, as it's under development ;)

But I think it will be fixed for the final release, because there is one developer working hard in the Internet Roaming spec, and that's why we have now NM by default :)

Regards
Pochu

---

### Post by Mr. Eddy on 2007-02-04
I had the same problem in dapper and I know someone who has it in edgy. but I discovered that the network manager in add/remove aplications doesn't work. Instead you have to load the networkmanager by rightclicking on your panel > add to panel > System & Hardware > network manager.

I don't know if this has something to do with your problem.

But if it is, it means that the network manager in add/remove aplications has to be removed out of the list or fixed. Because it doen't work in edgy and dapper too.

---

### Post by pochu on 2007-02-04
Network-Manager is, since Feisty, installed by default, so there is no need to install it from add/remove, because it's installed :D

---

### Post by Mr. Eddy on 2007-02-04
aah ok. sorry, I better shut my mouth when it's about a release I never used :)

---

### Post by pochu on 2007-02-04
No problem ;)

---

