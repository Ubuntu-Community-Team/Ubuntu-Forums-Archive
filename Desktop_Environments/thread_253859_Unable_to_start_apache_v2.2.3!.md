---
title: "Unable to start apache v2.2.3!"
date: 2006-09-09
forum: Desktop Environments
---

### Post by johnusa on 2006-09-09
I am running ubuntu 6.06 on my PC. I downloaded and installed the apache server ver 2.2.3 from source via the configure, make, and make install.  The apache2 package on my PC via synaptic package manager is ver 2.0.55.  At one point, ver 2.2.3 was working.  I then set apache2 to startup at boot.  Instead of ver 2.2.3, I was getting v2.0.55.  I then went to the synaptic package manager and removed v2.0.55.  When I go to the directory where apachectl (v2.2.3) is located and issue "./apachectl start", I get the following message:

> httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(13)Permission denied: make_sock: could not bind to address [::]:80
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs



I am new to linux and don't know what is wrong.  In addition, when I am in the directory where apachectl is located, I have to precede the command with "./" otherwise I get the message command not found.  I assume it's because the directory with apachectl is not in the path.

Can anyone tell me what I need to do to get apache v2.2.3 started.  I would also like to have it start at boot, also.

Thanks in advance for any help you can provide.

---

### Post by johnusa on 2006-09-09
Any suggestions?

---

### Post by johnusa on 2006-09-09
Never mind!  I have resolved this problem!

---

### Post by armware on 2006-10-24
how?

---

### Post by armware on 2006-10-24
turns out all i needed was a folder called 'logs' in the root dir of the hosted files (/var/log/www/). i'm not sure if i needed to create the file 'error.log' in the 'logs' folder or not, but doing so caused the problem to go away. after creating said folder and file, run sudo /etc/init.d/apache2 restart and i'm back up and running.

---

