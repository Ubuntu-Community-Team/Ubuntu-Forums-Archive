---
title: "search for wireless"
date: 2009-05-09
forum: General Help
---

### Post by caldoverde on 2009-05-09
Hi, here's my problem:

when I suspend my session on my ubuntu 9.04,when I log back in, sometimes the system won't log back to the internet because it doesn't find/search for the wireless connection. The only way I found to make the wireless connection is by restarting the computer.
I wonder if there is a way to make the computer search for the available wireless connections without rebooting??

Thanks

---

### Post by soro2005 on 2009-05-09
Does it not work if you wait a little? You can give it a kick in the butt with, in a terminal
```
iwlist scan
```
If, for some reason, networking or the network manager crashes when you logout/login (which shouldn't happen, but may, for instance if you hibernate) you can restart everything without rebooting the computer with 
```
sudo /etc/init.d/networking force-reload && sudo /etc/init.d/network-manager force-reload
```
If you need to do this regularly, you can make a script or a button with the command.

---

