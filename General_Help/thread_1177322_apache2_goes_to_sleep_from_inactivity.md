---
title: "apache2 goes to sleep from inactivity?"
date: 2009-06-03
forum: General Help
---

### Post by dirtmaster88 on 2009-06-03
I'm in the process of converting one of our older suse servers to ubuntu server 8.04. This server hosts a small webpage for internal use using apache2. If nobody views the webpage for about 20 minutes, it appears that apache goes into some kind of sleep mode. When I try going to the address, it can't find the server and just tries an internet search on it. If I try again it gets to the proper page right away. Is there any setting I overlooked in apache to eliminate the network activity monitor or something similar?

Thanks!
Nick

---

### Post by nikgare on 2009-06-03
Have you looked in the logs to see what's going on? I'd be very surprised if apache had a sleep mode!

The logs are in /var/log/apache2/

---

### Post by dirtmaster88 on 2009-06-03
> **nikgare said:**
> Have you looked in the logs to see what's going on? I'd be very surprised if apache had a sleep mode!

The logs are in /var/log/apache2/

Nothing out of the ordinary in the logs.

error.log
[notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations

---

