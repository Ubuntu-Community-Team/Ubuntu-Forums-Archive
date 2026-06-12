---
title: "Im just so good at having problems"
date: 2009-06-10
forum: General Help
---

### Post by LifeEscalade on 2009-06-10
So, I go in, edit some lines and now when I try to restart apache I get: (13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down; with a fail where the OK should be. Anyone know what's going wrong or what i'm doing wrong?

---

### Post by zcecc22 on 2009-06-10
Do you have any instance of apache crashed in the background blocking port 80? Do you have any other application which could be blocking port 80 (ie Skype). Finally do you have permission to start apache (sudo/root used?).

---

### Post by LifeEscalade on 2009-06-10
It probably has crashed in the past, and yes I do have permission (sudo used) but its still up to me at least. Could you check as well?

its [http://lolhoomin.hopto.org/wakaba.pl](http://lolhoomin.hopto.org/wakaba.pl)

---

### Post by nikgare on 2009-06-10
Which lines in which file did you edit?

---

### Post by LifeEscalade on 2009-06-10
oh boy. I wish I remembered, but it all seems to be working now. I just need to find docs on setting up the site to mysql. Havn't found nicely done docs yet.

---

