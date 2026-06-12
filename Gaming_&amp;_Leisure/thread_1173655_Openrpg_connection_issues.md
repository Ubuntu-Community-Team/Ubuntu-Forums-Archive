---
title: "Openrpg connection issues"
date: 2009-05-30
forum: Gaming &amp; Leisure
---

### Post by Lethys on 2009-05-30
While I can see the server list on openrpg, I am unable to connect to any of them.  However, when I try to do this on my windows install, with all other things the same, I am able to connect just fine.  I'm using a wireless Linksys WUSB54G v4 adapter, and can connect to the internet just fine.  Any help or even information on why would be appreciated.

---

### Post by Lethys on 2009-05-30
I have attempted this again on a wired connection and the problem still persists.  Further, attempts at joining a server on a different program, maptools, also ends in failure.  Checking through he documentation for openrpg, I came across info for this problems, stating that I needed to configure the firewall to allow openrpg to connect to port 6774.  I have no idea how I would go about doing this.  This is a fresh install of Ubuntu, and I have installed no firewalls myself.

---

### Post by Valon Majere on 2009-07-15
Im having this problem with openrpg as well anyone found a solution?

---

### Post by Kale the Quick on 2009-08-03
I am also having this problem. does anyone have any clue where to even start?

---

### Post by Woojoo//.deb on 2009-08-11
i had also some problems getting it running i then made a firewall exception and added a portforwarding which solved my problem then.
i would guess that you also need to forward your ports to get orpg running outside an local network.

---

### Post by Crakkerjakk on 2009-09-07
OK, so which ports need to be forwarded (the four digit number at the end of the server IP address after the colon?) and how does one make a firewall exception in a router?

---

### Post by Woojoo//.deb on 2009-09-08
[http://portforward.com/](http://portforward.com/) there you might find help for the forwarding the normal port is the four digit number at the end of the ip i guess it should be 9090 or something like that.

---

