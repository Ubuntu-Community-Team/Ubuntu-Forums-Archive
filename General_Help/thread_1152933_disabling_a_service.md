---
title: "disabling a service"
date: 2009-05-08
forum: General Help
---

### Post by StOoZ on 2009-05-08
Im running an FTP server (proFTPD) , now , whenever I turn the system on , it runs the daemon (proftpd) , and because I dont need it to be running most of the time , I stop it with 
sudo ./etc/init.d/proftpd stop

so how can I make it permanent without the need to uninstall it???
(I want to turn it off, until I explicitly decides to turn it on..)

---

### Post by Legace on 2009-05-08
Check if the service exists in System -> Preferences -> Startup Applications.

If not, then follow this guide (be careful):
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

