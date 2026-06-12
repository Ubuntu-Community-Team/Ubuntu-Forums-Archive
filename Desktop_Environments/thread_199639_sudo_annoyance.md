---
title: "sudo annoyance"
date: 2006-06-19
forum: Desktop Environments
---

### Post by bjourne on 2006-06-19
I have a server that I need to administrate remotely. Normally (with non-Ubuntu machines), if I would want to change the NIC definitions of it I can use emacs. I just find the file /root@1.2.3.4:/etc/network/interfaces and do my changes and then save the file.

But with Ubuntu this doesn't work. Because there is no root-user I can't get write-access to the file without sudo-opening it. So I can't use emacs. Instead I have to use a more tiresome process to update the interfaces file: 1. start a shell. 2. ssh to the machine. 3. sudo nano /etc/network/interfaces I have to use nano because on the server emacs isn't installed.

Maybe I have missed something. To me, sudo is more often than not just a big PITA.

---

### Post by Luke771 on 2006-06-19
[double-posted, sorry]

---

### Post by Luke771 on 2006-06-19
There *is* root, it's only disabled by default.
What you need is to run (locally)
```
sudo passwd root
```
and enter your root password 3 times (one when confirming that you have right to perform administrative tasks, two to enter and re-anter password)
then go to Start Menu/system/Administration/Login Screen and enable both root login and remote login.

---

### Post by aysiu on 2006-06-19
You can also just type ```
sudo -s
``` and that gives you a root prompt.

---

