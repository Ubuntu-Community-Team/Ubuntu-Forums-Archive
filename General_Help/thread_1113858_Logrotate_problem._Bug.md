---
title: "Logrotate problem. Bug?"
date: 2009-04-02
forum: General Help
---

### Post by marchost on 2009-04-02
I rarely post in forums for help but this one is driving me nuts.

I was monitoring my server and I saw that for a few hours the CPU would top at 100%. I pinpointed the problem to logrotate.


Here is the output of logrotate -vf /etc/logrotate.conf 

root@portafixeweb1:~# logrotate -vf /etc/logrotate.conf 
reading config file /etc/logrotate.conf
reading config info for /var/log/wtmp 
reading config info for /var/log/btmp

It get stuck there... I commented out the logrotate.d in this example. If I remove the btmp lines in logrotate.conf it get stuck at wtmp.

What I did as well : 

apt-get remove/install logrotate
dpkg-reconfigure logrotate

same problem after...

Any idea?

---

### Post by marchost on 2009-04-02
I forget to say that when logrotate get stuck, the cpu is running at 100%.

Also, I removed /etc/cron.daily/logrotate until I fix the problem

---

