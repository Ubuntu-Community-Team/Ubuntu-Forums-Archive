---
title: "MySQL Problem"
date: 2006-09-03
forum: Desktop Environments
---

### Post by reepsmac on 2006-09-03
Ok, first off I would like to say hi.  I have been using Ubuntu (breezy) for about 6 months now as a LAMP server and I have really enjoyed using it.  

My problem is that I am trying to connect to MySQL from my WinXP machine using the MySQL Query Browser, it wont connect and displays the error message: MySQL Error Number 2003 Cant connect to MySQL Server on port 192.168.1.104 (10061).  So after seeing this I was thinking that maybe the port that it runs on was blocked.  I ran a port scan on my ubuntu machine running MySQL both from ubuntu and from windows.  When I ran the port scan in Ubuntu the port MySQL operates on (3306) was listed as open.  When I ran the port scan from windows targeted at the same computer, port 3306 was not listed as an open port?  Could this be the cause of the problem and if so how can it be fixed?

---

### Post by mssever on 2006-09-03
By default, mysql only listens on localhost (the computer it's installed on). You need to edit /etc/mysql/my.cnf and comment out the bind-address line.

Then, restart mysql: ```
sudo /etc/init.d/mysql restart
```

---

