---
title: "networking problems"
date: 2006-08-26
forum: Desktop Environments
---

### Post by MaximumMax on 2006-08-26
i am trying to get dhcp to dish out an ip addresses to another pc. I set up the 
ethernet adapters on my original install to read the ethernet 1 as the primary adapter and when i set up the priorities showing it as the gateway it gets a connection to the internet but setting up the intranet connection it wont give the second pc a dhcp address. i have also tried to set it up manually. I understand that in ubuntu the dhcp is not installed for servering
out ips and have installed dhcp in root or at least i think i did...this is all like a foreign road map.I have read the online and operating system help but still cant get it to give a dhcp address to the second machine

---

### Post by v1ct0r on 2006-08-26
Have you tried changing the MAC address ? 

ifconfig eth0 down hw ether 00:00:00:00:00:01
ifconfig eth0 up

---

