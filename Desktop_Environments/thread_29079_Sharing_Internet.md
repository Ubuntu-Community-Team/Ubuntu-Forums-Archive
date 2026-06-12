---
title: "Sharing Internet"
date: 2005-04-22
forum: Desktop Environments
---

### Post by Ubuntu_User on 2005-04-22
I need to share the internet from my XP box to my Ubuntu box. Here is my configuration.

I have my XP box connected to the linux one with a crossover cable. The XP box is currently running on a usb linksys nic.

I have the wireless card set to share it's internet through the LAN. I get an ip in Ubuntu and can ping any ip in the network but I can't get internet. Any help would be appreciated. Thanks

---

### Post by shakin on 2005-04-22
[QUOTE=Ubuntu_User]I need to share the internet from my XP box to my Ubuntu box. Here is my configuration.

I have my XP box connected to the linux one with a crossover cable. The XP box is currently running on a usb linksys nic.

I have the wireless card set to share it's internet through the LAN. I get an ip in Ubuntu and can ping any ip in the network but I can't get internet. Any help would be appreciated. Thanks[/QUOTE]

when you say you can't get to the internet, what does that mean? Can you ping or browse an IP like 216.239.39.99 (google)? If you can hit the IP but not the domain, you will need to manually add your ISP's DNS servers in /etc/resolve.conf using this format:

nameserver 000.000.000.000

You can add lines for more than one.

Actually, if you don't want to edit resolv.conf you can go to System / Administration / Networking and use the DNS tab in the GUI.

---

### Post by Ubuntu_User on 2005-04-22
Thanks for the help! I had the DNS set to the XP machines ICS ip rather than my routers DNS.

---

