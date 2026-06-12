---
title: "phpMyAdmin Access Denied"
date: 2009-02-27
forum: General Help
---

### Post by VengefulIce on 2009-02-27
Hi all,

I have been trying to set up the servers in Ubuntu following the guide found at the site: [http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06](http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06)

Everything works fine up until the part about testing myphpadmin.  I get the login screen and everything, but when i type in root as my user and my password, it shows the following error: 

"#1045 - Access denied for user 'root'@'localhost' (using password: YES)"

I would appreciate any help on this situation

Thanks

---

### Post by iaculallad on 2009-02-27
Try to test your MySQL root account using the terminal by issuing the command below:

```
mysql -u root -p
```

Does it display the same error message?

---

### Post by VengefulIce on 2009-02-27
Yeah it still shows the same thing

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

---

### Post by Peter09 on 2009-02-27
This means your password is incorrect. I always found this error message confusing. The *Using Password YES* bit just means that your have used a password.

---

### Post by iaculallad on 2009-02-27
> **VengefulIce said:**
> Yeah it still shows the same thing

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

You are inputting incorrect 'root' password. Try to reset your MySQL password:

Stop your MySQL server:

```
sudo /etc/init.d/mysql stop
```

Access your MySQLd configuration:

```
sudo mysqld --skip-grant-tables &
```

Replace your old password:

```
UPDATE user SET Password=PASSWORD('YOURNEWPASSWORD') WHERE User='root'; FLUSH PRIVILEGES; exit;
```

---

### Post by VengefulIce on 2009-02-27
Ok thanks

I will try that when I get home

---

### Post by VengefulIce on 2009-02-27
Ok so i tested the reset password method, and it tried logging in again, and it still shows the same error message.

#1045 - Access denied for user 'root'@'localhost' (using password: YES)

are there any other possible causes for the error to appear?

---

### Post by Hobgoblin on 2009-02-28
Unless you set it during the install, there is no root password (for MYSQL).

Don't confuse MYSQL root with Linux root.

---

### Post by VengefulIce on 2009-03-02
Well I set a password and it didn't work, so i tried resetting the password and it still doesnt work

---

### Post by VengefulIce on 2009-03-02
ok everything works fine now, i just reset the password to something different

---

