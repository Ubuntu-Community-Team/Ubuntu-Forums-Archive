---
title: "Samba, VNC not working"
date: 2006-08-27
forum: Desktop Environments
---

### Post by Lary Grant on 2006-08-27
I am having a hard time setting up Samba and VNC between 2 PCs, both running Dapper, connected to each other via a wireless router.  They are both plugged in to the router with a cable, so they are not wireless.  The router is connected to a DSL modem, in case that matters.

It seems that the 2 computers just cannot see each other at all.  1 cannot see the other on the Samba network and if I type the IP address into VNC it cannot connect.  Although oddly enough, if I connect to the wireless network with a laptop running Windows XP and WinVNC, I can connect to VNC fine.  Go figure.

---

### Post by gerbman on 2006-08-27
Can you ping each computer from the other? If you can't, check the router setup and any firewalls you have running. Once you can ping each computer, you can use [this]("http://ubuntuforums.org/showpost.php?p=1265314&postcount=2") setup for Samba.

---

