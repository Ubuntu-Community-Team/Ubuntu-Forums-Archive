---
title: "phpmyadmin MysQL DEactivated"
date: 2006-08-03
forum: Desktop Environments
---

### Post by hansi70 on 2006-08-03
Hi,

I have installed xampp with phpmyadmin. When I use the firestarter firewall before initiating xampp (i.e. lampp start), the status of MYSQL is displayed as DEACTIVATED and tetsing the mysql from the shell prompt also shows that MYSQL is not running.

I assume that this error is a result of the firewall blocking MYSQL 5 server from accessing a certain port.

My question is:

How can I determine what port number mysql is using and how can I unblock it in firestarter?

Your help will be appreciated,

Hansi

---

### Post by bmonkey on 2006-08-03
try using the mysql default port which is **3306**

Have you tried manually starting it?

---

### Post by hansi70 on 2006-08-27
Hi,

Thank you for your reponse. Apologies for the delay in responding. I have been away on a long holiday. I fixed the problem. It seems that Firestarter was blocking the MySQL port. As soon as I closed firestarter and restarted the LAMP application everything worked fine.

Regards,

Hans

---

