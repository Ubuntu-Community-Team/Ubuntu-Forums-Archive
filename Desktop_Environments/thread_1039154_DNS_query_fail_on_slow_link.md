---
title: "DNS query fail on slow link"
date: 2009-01-14
forum: Desktop Environments
---

### Post by kstan_79 on 2009-01-14
Hi,

I facing problem on DNS query time out too short on Ubuntu Linux. Anybody can solve it?

The scenario as below.
1. When I start download big file from internet, I can't go to any website anymore due to DNS time out(It return to me destination host not found).

2. However when I direct connect any internet webserver or ISP DNS server via ip address, I can get reply.

3. This problem will disapear when I stop downloading file.

4. When I download file from internet, computer beside me(Using Ubuntu 8.04 or 8.10) can't query the DNS as well. However windows PC not effected. Ubuntu PC beside me can reach internet webserver via IP address as well.

5. Currently I been force to put some record in /etc/hosts file to solve this problem.

Any expertise can help me??
Plus: I'd setup DNS server in my PC and I query my DNS server as well, it doesn't help.
Regards,
Ks Tan

---

### Post by kstan_79 on 2009-01-20
Nobody having this problem? or nobody know how to solve it?

---

### Post by x33a on 2009-01-20
most probably all of your bandwidth is being used by you download program. try limiting the speed of your downloads, and you'll be able to surf the net.

---

