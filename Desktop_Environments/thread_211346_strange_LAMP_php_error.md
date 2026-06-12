---
title: "strange LAMP php error"
date: 2006-07-08
forum: Desktop Environments
---

### Post by tefflox on 2006-07-08
I used scp to copy files to localhost.  One of them throws this error, but the other pages, which are nearly identitcal, work fine. What does this mean? It is a copy of the page [http://listenlight.net/00/](http://listenlight.net/00/)

[php]Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning:  Unknown: Failed opening '/var/www/00/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0[/php]

---

### Post by mgor on 2006-07-08
and what are the permissions for /var/www/00/index.php?

---

### Post by tefflox on 2006-07-08
thanks.. chmod og+r fixed the problem

---

