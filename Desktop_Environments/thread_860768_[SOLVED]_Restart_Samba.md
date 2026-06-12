---
title: "[SOLVED] Restart Samba"
date: 2008-07-15
forum: Desktop Environments
---

### Post by TheGreatandMightyMe on 2008-07-15
I'm trying to get my windows machine to share files with my ubuntu machine so I have just installed Samba.  I had to go in and change the config file but now I want to restart the daemons without rebooting the machine.  How can I interface with the daemons.

Thanks

---

### Post by NikoC on 2008-07-16
In a terminal:

sudo /etc/init.d/samba restart

This will restart samba...

Cheers.

---

