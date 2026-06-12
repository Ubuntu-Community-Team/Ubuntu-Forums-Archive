---
title: "RP-PPPoE connects, but no ping"
date: 2006-01-19
forum: General Help
---

### Post by MblKiTA on 2006-01-19
I'm using RP-PPPoE to connect to my adsl provider. It connects to it, but I can't load any web page and there is no ping replies from any of the web servers.
Only if I do "*route del default*" before setting up the connection, everything works, but when I do this I can't see parts of our LAN after the router. So what is the best way to configure PPPoE connection correctly? Thanks.

---

### Post by MblKiTA on 2006-01-20
?

---

### Post by peluso on 2006-02-07
Check your DNS at /etc/resolv.conf or system -> Administration -> Net

I have a modem bridge speed stream conected to my NIC eth0

configuration ethO
IP=172.16.0.2 
netmask=255.255.0.0
gateway=10.0.0.1
dns=200.23.242.193 (warning: this dns is only for telmex users in Mexico look for your DNS at your country).

---

