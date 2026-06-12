---
title: "Transmission quick question"
date: 2009-06-06
forum: General Help
---

### Post by lucifuge on 2009-06-06
I've managed to open port 51413 with both UPnP and NAT enabled, and it's port forwarding. With an ADSL2+ connection of  1500kbs  download, I was getting download speeds of approx 250kbps in Bittorent in XP. In Ubuntu /Transmission, I'm getting a max of around 30kbs. Seems very low for the port in an OPEN state and the above features enabled. What can explain this?  is DMZ required?  currently that is disabled.  

I just can't see what else to do...but something aint right!

---

### Post by lovinglinux on 2009-06-06
Maybe you have the Transmission blocklist enabled, so you could be connected to less peers.

I would recommend Deluge. It has Windows and Ubuntu versions, lot's of features and it's easy to configure. The best client in my opinion.

Deluge is in the repositories, but you can get the latest version and add it's own repository at [http://dev.deluge-torrent.org/wiki/Download](http://dev.deluge-torrent.org/wiki/Download)

---

### Post by lucifuge on 2009-06-06
> **lovinglinux said:**
> Maybe you have the Transmission blocklist enabled, so you could be connected to less peers.

I would recommend Deluge. It has Windows and Ubuntu versions, lot's of features and it's easy to configure. The best client in my opinion.

Deluge is in the repositories, but you can get the latest version and add it's own repository at [http://dev.deluge-torrent.org/wiki/Download](http://dev.deluge-torrent.org/wiki/Download)


Deluge rocks!!  thanks for your advice, much obliged.

---

### Post by ActiveFrost on 2009-06-06
Regarding your speed issues, check Preferences - there's a place where you can change max peers per torrent, etc. ( which could be the reason why you get such a low speed ).

---

### Post by lovinglinux on 2009-06-06
> **ActiveFrost said:**
> Deluge is good, but, it does not have a web interface ( Transmission has ) :p

What? Deluge has web interface with several options, including an ajax interface. It also has remote gtk, which allows you to run the graphical interface frontend locally and connect to a remote daemon. That's it? No. You can also use cli :)

Deluge beats Transmission in almost every aspect. Maybe not in performance, but it's getting better.

---

### Post by ActiveFrost on 2009-06-06
> **lovinglinux said:**
> What? Deluge has web interface with several options, including an ajax interface. It also has remote gtk, which allows you to run the graphical interface frontend locally and connect to a remote daemon. That's it? No. You can also use cli :)

Deluge beats Transmission in almost every aspect. Maybe not in performance, but it's getting better.

Hmm .. wasn't able to find it :o Will check it out again a bit later on today ! Thanks for the info ;)

---

### Post by lovinglinux on 2009-06-06
> **ActiveFrost said:**
> Hmm .. wasn't able to find it :o Will check it out again a bit later on today ! Thanks for the info ;)

You need to install [deluge-console](apt:deluge-webui) [deluge-webui](apt:deluge-webui).

How to use at [http://dev.deluge-torrent.org/wiki/Faq](http://dev.deluge-torrent.org/wiki/Faq)

---

