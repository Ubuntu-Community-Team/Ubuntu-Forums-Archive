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

### Post by jstrubberg on 2005-10-24
You need to type:

#mysql -u root -p <enter>

Then key in the root password.

---

### Post by mgor on 2005-10-24
[QUOTE=heart_reaver]
NO Configuration
For a website or so like
localhost 
and one more that i dont remenber 
[/QUOTE]

that was some settings for postfix.
mysql-server depends on mailx, which depends on a mail-transport-agent, so installing mailx triggered dpkg to configure a mail-transport-agent if it hasen't been done before.

---

### Post by heart_reaver on 2005-10-25
[QUOTE=mgor]that was some settings for postfix.
mysql-server depends on mailx, which depends on a mail-transport-agent, so installing mailx triggered dpkg to configure a mail-transport-agent if it hasen't been done before.[/QUOTE]

Thanks for info. but i am not able to confgure it can you help on it. One thing i forget to mention is, I got some text writen on first screen of confguration 
For reconfiguring postfix configuration of mysql 

**dpkg-reconfigure --priority=low postfix **

i got confguration file in that i have selecter option four

Local only

Then i get where root mail should go

--------------------
root  
---------------------


then "mail name "
----------------------------
root@amnesty
----------------------------

other destination for mails

-----------------------------------------------------------------------------------
amensty.hotwire.com, locahost.hotwire.com,locahost,amnesty
-----------------------------------------------------------------------------------

Force synchronous for update mail queue ?

YES

more details are there in screensots attached plz tell what to do ](*,)

---

### Post by heart_reaver on 2005-10-25
[QUOTE=jstrubberg]You need to type:

#mysql -u root -p <enter>

Then key in the root password.[/QUOTE]

my friend it is asking for password 

root@amnesty:~# mysql -u root -p
Enter password:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)
root@amnesty:~#

that i enter is of root, user. there is no use of it. Think it is not even able to recongnize root as user

when i tried: mysqladmin -u root password db_user_password

[B]
root@amnesty:~# mysqladmin -u root password hello
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'
[/B]

---

### Post by mgor on 2005-10-25
hm, mailname should only be a domain, in your case 'amnesty'.
seems like you've already set a mysql root password. to reset it follow this guide
[http://dev.mysql.com/doc/refman/4.1/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/4.1/en/resetting-permissions.html) (look under " In a Unix environment, the procedure for resetting the root password is as follows").

---

### Post by heart_reaver on 2005-10-25
thanks mgor  it works 

thanks to jstrubberg too :D

---

