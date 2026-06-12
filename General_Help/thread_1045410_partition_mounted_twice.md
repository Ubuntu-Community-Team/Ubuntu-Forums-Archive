---
title: "partition mounted twice"
date: 2009-01-20
forum: General Help
---

### Post by irakli_san on 2009-01-20
hello

just 1 months ago i installed ubuntu 8.04 x64. have no experience!

i have edited /etc/network/interfaces, trying to make network brigde
from two network ports but i ended with linux crash.(my fault :))
i heve restoring this file and it works fine but now i have file system partition and same partition in file browser as "27.8 GB Media". i know there may be no connection between this two behaviors. i just want to be like it was before.

and is there any "guied" solution of configuring network bridge for not advanced users?

thanks

---

### Post by svennils on 2009-01-20
Are you trying to make the machine route packets between 2 network cards, on separate networks?

---

### Post by irakli_san on 2009-01-20
i don't know. i just followed this steps from
[http://ubuntuforums.org/archive/index.php/t-132515.html](http://ubuntuforums.org/archive/index.php/t-132515.html)

[HTML]its even easier in linux. just add
iface br0 inet dhcp
bridge_ports eth0 eth1

to /etc/network/interfaces
then reboot, run terminal and run sudo ifup br0.[/HTML]

---

### Post by dragos_iliescu_2005 on 2009-01-20
You ask here for two problems that came separately:
1. mount twice, check /etc/fstab what mounting points are defined there. Edit the file if you need.

2. making the bridge. Why you need bridging?

---

### Post by irakli_san on 2009-01-20
thanks.

i have two computers and don't have switch or hub. guess buying a switch will be best solution for me.

---

### Post by dragos_iliescu_2005 on 2009-01-21
Ok, search for a router (wire or wireless) - is the best solution. Price are OK. I have the same configuration at home with 2 PCs., 1 laptop.

---

