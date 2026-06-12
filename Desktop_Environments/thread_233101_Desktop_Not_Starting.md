---
title: "Desktop Not Starting"
date: 2006-08-09
forum: Desktop Environments
---

### Post by bitwise on 2006-08-09
I have a dual boot system with Windows 2003 Server, and recently tried booting into Ubuntu. I get to the graphical login screen and enter username/pw, it accepts it, and then just goes to a black screen with my cursor.

I tried ctrl-alt-f1 to get to a terminal, it worked, and i checked error logs, but couldnt find anything.

any suggestions?

---

### Post by mg3kc on 2006-08-09
update your system from the terminal...

sudo apt-get update
sudo apt-get upgrade

see if it throws up anything new that you should install?

---

### Post by rkstanton on 2006-08-23
Did this help? I have the same issue. I don't see any other similar posts.

---

### Post by leb3000 on 2006-08-24
could it be the recent Xorg update broke your ubuntu?

---

