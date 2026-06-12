---
title: "Ubuntu Desktop as a Client and Server OS"
date: 2006-07-21
forum: Desktop Environments
---

### Post by agajardo on 2006-07-21
This question is directed towards experienced users..

I am interested in installing the Ubuntu Linux distribution on a single computer that will act as a server to a private network of 1 to n desktop clients (each running windows) and I want to know whether there exists any significant difference between Ubuntu Server and Desktop versions in terms of, say, playing the role as a Linux server OS..

I guess what I am saying is that if the Desktop version includes all features available in the Server version (and more, i.e. GUI interface), then I would prefer to install the Desktop version.  HOWEVER, if this is NOT the case, then I would obviously have to go with the Server version.

Any comments?

---

### Post by cptnapalm on 2006-07-21
The only fundemental difference, I think, is that the server version installs a server kernel, which is NOT good for desktop use.  Assuming that you are only going to have it serve as a DHCP and/or mail and/or web then running it on the desktop version will be no problem, I don't think.

I've got Apache2, MySQL, OpenLDAP(though I can't find a damn bit of documentation on how to use it), Postfix and a bunch of other daemons running .  And this is a mid-range laptop.

The only advice would be to slap as much RAM in as you can.  RAM for a server is Good.

---

