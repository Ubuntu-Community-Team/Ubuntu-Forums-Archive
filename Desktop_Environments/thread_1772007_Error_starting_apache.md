---
title: "Error starting apache"
date: 2011-05-31
forum: Desktop Environments
---

### Post by lucacerone on 2011-05-31
Hi everybody,
I've experienced a few issue installing a LAMP server on my Ubuntu 11.04.
I've installed it using the "LAMP" task from Synaptic.
As I couldn't get Apache to run .php paged I've tried
to modify a few times the apache2.conf and other
files till I got stuck.
So I decided to purge the apache2 and other packages
and to reinstall them.

After I've done this, whenever I try to start the apache2 server
( sudo /etc/init.d/apache2 start )
I get the following error:

> (98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down

Can you help me fix the problem and start apache again?
Thanks a lot in advance,
Cheers, -Luca

---

