---
title: "Configuring Azureus as BitTorent"
date: 2006-08-04
forum: Desktop Environments
---

### Post by navid on 2006-08-04
Hi
I have installed Azureus but I have the NAT problem but I can use BitTorent so easily and with no problem. I thought maybe I could use the same port as for BitTorent? Has anyone configured Azureus in Dapper? It's really a nice app, surely much better than Ubuntu's default torrent app.

---

### Post by MerZo on 2006-08-04
> **navid said:**
> Hi
I have installed Azureus but I have the NAT problem but I can use BitTorent so easily and with no problem. I thought maybe I could use the same port as for BitTorent? Has anyone configured Azureus in Dapper? It's really a nice app, surely much better than Ubuntu's default torrent app.

Azureus is an BitTorrent client and therefore you can use the same port for the program as you use for the other one.

---

### Post by mcman42 on 2006-08-04
Yup, it is really a nice app. You can set up Azureus to use the same port as the bittorent does or you can allow traffic on Azureus default port in your firewall if you have one installed. It is up to you.

---

### Post by msandersen on 2006-08-04
I'm using Azureus. Originally I followed a HowTo,  but since tried Automatix for the hell of it; it's method is based on the same HowTo. The only thing I had to do differently was chmod the folder /opt/azureus to 665 so updates could install, and I also chowned to root:admin.

I've set port forwarding on my router/modem to port 49152, which I chose to use in Azureus after reading their site docs. It needs to be set for *both* UDP and TCP.

---

