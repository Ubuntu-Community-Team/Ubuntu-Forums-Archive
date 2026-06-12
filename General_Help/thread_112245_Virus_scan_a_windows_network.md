---
title: "Virus scan a windows network"
date: 2006-01-03
forum: General Help
---

### Post by Masteroc on 2006-01-03
Hi,

Just wondering if it is possible to have an ubuntu machine virus scan, or protect a windows network. The ideal setup would be to have an ubunut machine somewhere on the network. While the windows machines and workers go about their buisness, they ubuntu machine would virus scan each one, or maybe just the stuff coming into the network such as downloads. Is there any way to do this?

~Masteroc

---

### Post by chocolatetoothpaste on 2006-01-03
I have a ubuntu machine with 2 network cards: 1 for the internet and 1 for the LAN.  I have a DSL modem, and i downloaded and installed firestarter on the linux machine.  I enabled internet sharing, and even setup to run a dhcp server, so every time a computer connects to the network, it receives an ip, etc.  It is great for internet sharing with firewalling/traffic filtering.  You could use wine, and cron to schedule it to scan all the win boxes, but I don't know how you would make it work.  If you are interested in a firewall setup though, I can post more details about my setup.

---

### Post by Masteroc on 2006-01-04
i was looking for something where i can just have this computer in the back room and have it do this. The whole dhcp server thing is a bit out of my leage and i dont want to even attempt this. Is there any other way?

---

### Post by le_jawa on 2006-01-04
I've seen Clam AV as a popular open-source solution.  I can't help you with it, but you can check it out at [http://www.clamav.net/abstract.html#pagestart](http://www.clamav.net/abstract.html#pagestart) .  

It seems like a read a review at some point indicating that there are more robust Linux solutions out there, but they are proprietary.   I don't know if you are against paying for this or not.

---

