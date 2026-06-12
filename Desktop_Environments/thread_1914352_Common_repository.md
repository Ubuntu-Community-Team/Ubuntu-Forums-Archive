---
title: "Common repository"
date: 2012-01-24
forum: Desktop Environments
---

### Post by samkct on 2012-01-24
Hi;
 
I wish to know if there any patch management service on Ubuntu;
 
A method to store the security updates on the network so that multiple machines point to the same rather than internet.
A way to enforce this rule so that all clients can point o the share drive.
 
Regards
SD

---

### Post by Lars Noodén on 2012-01-24
apt-cacher and apt-cacher-ng allow multiple machines to download  once from the net and then subsequent downloads occur from the local cache.  You have to make some small changes to the local machines, either in the source.list file or in apt.conf.d

[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

---

