---
title: "Firestarter prevents LAN Printers from being detected by CUPS"
date: 2005-07-18
forum: Desktop Environments
---

### Post by jcohen on 2005-07-18
When Firestarter is enabled, gnome-cups-manager does not show my Epson C86 connected to my Debian Sarge server. My firestarter policy allows connections on port 631 by everyone and allows connections from 192.168.0.4 which is the IP of the print server. I see nothing in the events tab that would suggest packets are being blocked. The only solution is to stop the firewall. After doing so the Epson Stylus C86 is shown in gome-cups-manager in a matter of seconds.

I have used both Hoary's firestarter (1.0.1) and backports (1.0.3). I see the same problem in both. I was wondering if anyone here knows a solution to this problem. 

ii firestarter 1.0.1-1ubuntu2 gtk program for managing and observing your

/etc/firestarter/inbound/allow-from

192.168.0.4,

/etc/firestarter/inbound/allow-service

AOL IM, 5190, everyone,
Auth, 113, everyone,
VNC, 5900-5903, 192.168.0.4,
SSH, 22, 192.168.0.4,
eDonkey, 4662-4672, everyone,
Gnutella, 6346, everyone,
Ipp, 631, everyone,

---

### Post by arunsub on 2005-07-18
See if this helps
[http://ubuntuforums.org/showthread.php?t=25721](http://ubuntuforums.org/showthread.php?t=25721)

---

