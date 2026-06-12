---
title: "mysql problem"
date: 2005-10-23
forum: Desktop Environments
---

### Post by heart_reaver on 2005-10-23
Hi there,

I was installin mysql by 



At the time of installation i got some options to choose form they were :rolleyes: 

NO Configuration
For a website or so like
localhost 
and one more that i dont remenber 

Then i clicked on the second option 

Next screen shows message 

====================================================== 
news and mail messages (following the username and @ sign)

This name will be used by other programs besides Postfix; it should be the single, full domain name(FQDN) form which mail will appear to orignate.

Mail name?

-------------------------------------------------------
xyz.abc.com
------------------------------------------------------

< ok >          <cancel>

===================================================


Then for creating user i use

mysqladmin -u root password db_user_password

as per given on [http://www.ubuntuguide.com]("http://www.ubuntuguide.com")


Then this what i get 


=============================================

root@amnesty:~# mysqladmin -u root password db_user_password
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'
root@amnesty:~#

==========================================
:confused: 

When i wriite 

root@amnesty:~# mysql

i get 

=========================================

root@amnesty:~# mysql
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)
root@amnesty:~#

=========================================

Need urgent help 

Regards

heart_reaver

---

