---
title: "wireless dhcp server?"
date: 2006-03-10
forum: Desktop Environments
---

### Post by SSamiK on 2006-03-10
On a ubuntu box at home i want to use my wireless card as a dhcp server, so friends with laptops and pocketpc's can connect to my computer. I have tryed using the dhcp server setup in [http://ubuntuguide.org/#dhcpserver]("http://ubuntuguide.org/#dhcpserver") but the dhcp server fails to start... 

Attatched the dhcp.conf and the dhcp3-server files.

Since i'm quite a noob at linux, I really could need some help...


EDIT:  I've figured it out. The wireless card (wlan0) was set to obtain IP from a DHCP, it startet working when i set it to a static IP and restarted the DHCP server.

---

