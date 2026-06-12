---
title: "Network Bonding on Ubuntu Desktop 20.04"
date: 2020-05-28
forum: Desktop Environments
---

### Post by gourmetsaint on 2020-05-28
Long term ICT but my first foray into Linux. I have a home server which I have installed Ubuntu Desktop 20.04 for ease of setup for a newby. I have all my network shares and Plex running fine.


The server has dual 1Gb NICs. I would like to use bonding (mode 0) to take advantage of the bandwidth. The yaml file in netplan only has a couple lines and sets renderer to networkmanager. The /etc/modules file is empty.


What do I need to do to bond my two NICs?

Thanks in advance.

---

### Post by nick-kostov on 2020-06-03
Check my [https://ubuntuforums.org/showthread.php?t=2444718&highlight=bonding](https://ubuntuforums.org/showthread.php?t=2444718&highlight=bonding) .

---

### Post by gourmetsaint on 2020-06-04
I eventually worked it out. I needed to add to the .yaml file for the bond specs and used try function. The syntax is a little different from the networkd version. There are restrictions on parameter settings and it does not support "name gooping". Thanks for the help.

---

