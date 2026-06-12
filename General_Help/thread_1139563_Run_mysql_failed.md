---
title: "Run mysql failed"
date: 2009-04-27
forum: General Help
---

### Post by runnner on 2009-04-27
I following this link [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) to install LAMP.

After I installed Mysql, I typed following command into the termainl window.
mysql -u root

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Where is wrong, thanks in advance!

---

### Post by blazemore on 2009-04-27
I think it might be because mysql isn't allowing a root log in without a root password?
Is there an account "root"?
If there is, try adding a password to it.

---

### Post by sahabcse on 2009-04-27
Hi 

Try

#mysql -u root -p

For reseting the mysql password follow below url

[http://sahabm.blogspot.com/2009/03/access-denied-for-user-rootlocalhost.html](http://sahabm.blogspot.com/2009/03/access-denied-for-user-rootlocalhost.html)

---

### Post by runnner on 2009-04-27
> **sahabcse said:**
> Hi 

Try

#mysql -u root -p

For reseting the mysql password follow below url

[http://sahabm.blogspot.com/2009/03/access-denied-for-user-rootlocalhost.html](http://sahabm.blogspot.com/2009/03/access-denied-for-user-rootlocalhost.html)

I tried 
#mysql -u root -p

When "Enter password:" shows , I just press "enter" button, the it gives:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

The same error occured.

---

### Post by sahabcse on 2009-04-27
Hi

I think issue in mysql root user password. Have set the mysql password for root user?

---

### Post by runnner on 2009-04-27
I can't start mysql, I will try to reset password for root.

---

### Post by sahabcse on 2009-04-27
Pls follow below url


[http://sahabm.blogspot.com/2009/03/a...localhost.html](http://sahabm.blogspot.com/2009/03/a...localhost.html)

---

