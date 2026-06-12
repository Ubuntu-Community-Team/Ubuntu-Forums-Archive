---
title: "CS:GO Dedicated Server Ubuntu 14.04"
date: 2015-08-28
forum: Gaming &amp; Leisure
---

### Post by aliy2 on 2015-08-28
Hello, 
So i recently installed the CSGO dedicated server package on a dedicated ubuntu 14.04 server but unlike the past few times I've done it, only 50% of people can actually connect to the server. The server was installed correctly and there are no errors in console, but some people cannot connect and they keep receiving the error retrying public (INSERTIPHERRE:PORT). Even I myself cannot connect to the server although i can connect to SSH and all that. 

Thanks in advance, 
Ali

---

### Post by bizhat on 2015-08-28
Disable firewall and see if that works.

```

iptables -F

```

---

