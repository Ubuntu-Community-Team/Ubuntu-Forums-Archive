---
title: "ProFTPd"
date: 2005-11-08
forum: Desktop Environments
---

### Post by aaronshaf on 2005-11-08
I have ProFTPd installed. I can FTP from another computer in the network using the main login for the machine. How do I get it so that this user has permissions to change /var/www ? Thanks!

---

### Post by Ampersand on 2005-11-08
```
sudo chown -r *username* /var/www
```
should do it (replacing *username* with whatever the username is you want to give permissions to).

---

