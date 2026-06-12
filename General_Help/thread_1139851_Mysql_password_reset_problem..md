---
title: "Mysql password reset problem."
date: 2009-04-27
forum: General Help
---

### Post by runnner on 2009-04-27
I can't start mysqls client, get access denid error:
ERROR 1045 (28000): Access denied for user 'root'@'localhost', and I try to reset password of root. So I following the link below to reset the password.
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

Here is the steps:
```

1. sudo /etc/init.d/mysql stop
2. sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &
3. mysql -u root
4. mysql> SET PASSWORD FOR root@'localhost'=PASSWORD('newpassword');
ERROR 1290 (HY000): The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement

5. mysql> update mysql.user set password=PASSWORD('newpassword') where user='root';
Query OK, 3 rows affected (0.01 sec)
Rows matched: 3  Changed: 3  Warnings: 0

6. FLUSH PRIVILEGES;
7. sudo /etc/init.d/mysql stop
8. sudo /etc/init.d/mysql start


```
After these steps, I can start mysql client with root account, I can run sql commands now.

However there is an error occured at step 4, I don't know what caused this error. Thanks for help!

---

