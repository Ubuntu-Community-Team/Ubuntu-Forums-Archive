---
title: "Slow internet connection"
date: 2006-08-21
forum: Desktop Environments
---

### Post by breezey on 2006-08-21
Just installed Ubuntu Dapper Drake 6.06, and it works great. Got all my devices setup properly and everything runs smoothly. The only thing is my internet connection (browsing with Firefox) is very slow. And Google does not even turn up. I use static IP and I don't have speed issue for my intranet (I can send/receive file to/from other computer with normal speed).

Did I miss something here?

Thanks for your help.

PS: I also have updated my Ubuntu through live update.

---

### Post by breezey on 2006-08-22
Solved by putting the ISP's DNS-es. Thanks.

---

### Post by Zach1188 on 2006-08-22
In Firefox, type "about:config" in your address bar, and search for "ipv6". "network.dns.disableIPv6" should currently be set to false. Double-click it so it is set to true.

---

