---
title: "Firefox 1.5 deb"
date: 2006-01-08
forum: General Help
---

### Post by ScreemingBlue on 2006-01-08
For anybody wanting to upgrade to firefox 1.5, here is a deb from the Debian backports.

Add this line

> deb [http://www.backports.org/debian/](http://www.backports.org/debian/) sarge-backports main

to your /etc/apt/sources.list.

and run

> sudo apt-get update

then 

> sudo apt-get install firefox

---

### Post by myke on 2006-01-08
Or you can install it (& other goodies if you choose to do so) using [Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix").

---

### Post by bluebyt on 2006-01-08
Thank you, worked like a charm!

---

### Post by wallijonn on 2006-01-10
I'd wait until Mozilla fixed the memory leak problem.

---

