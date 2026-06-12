---
title: "MySql problem"
date: 2005-12-22
forum: General Help
---

### Post by kumakun on 2005-12-22
I'm having a bit of a problem with MySql I've installed everything from syanptec for the server and client and admin sides of it, as well as the mysql-admin gui frontend. Trying to start mysql or use the command mysqladmin in command prompt gives me this:
```
ERROR 1130 (00000): #HY000Host 'localhost.localdomain' is not allowed to connect to this MySQL server
```

Any thoughts? All the MySql forums I've gone to were either very windows platform oriented or very vague.

Thanks

---

### Post by paddyg on 2005-12-22
First of all i think you should set a password for your MySQl root account:
```
mysqladmin -u root password "yourpassword"
```
Then start mysql as root
```
mysql -u root -p
```
Then grant privileges to users (for example, if you want another superuser):
```
GRANT ALL ON *.* TO youruser@localhost IDENTIFIED BY "youruserpassword";
```
Hope it helps

---

### Post by kumakun on 2005-12-22
Nope. Returns the exact message on the first command. So this:
```
mysqladmin -u root password "yourpassword"
```

Returns this:
```
mysqladmin: connect to server at 'natsuko' failed
error: '#HY000Host 'localhost.localdomain' is not allowed to connect to this MySQL server'
```


Edit: When I used the actual command, I did replace "yourpassword" with the real password.

---

### Post by pheelay on 2005-12-22
try:
mysql -u root -h localhost -p

Probably /etc/hosts has an entry like
127.0.0.1 localhost.localdomain localhost

It seems the mysql client connects to the first entry in the list and mysql rejects it as an unknown domain. Swapping localhost.localdomain and localhost has fixed this effect for me in the past.

---

### Post by kumakun on 2005-12-22
Okay, getting closer I think. That returns this error: 

```
ERROR 1045 (28000): Access denied for user 'justin'@'localhost' (using password: YES)

```

Edit: Additionally it doesn't matter if I use root, mysql (which is in my.cnf) Or my account.

---

### Post by pheelay on 2005-12-22
Right. Would 'justin' have an account in MySQL.
Chances are during the mysql install the same problem occured and the password didn't get set. Try some of these to reset the root password:

mysqladmin -u root password "new_password"
mysqladmin -u root -h localhost password "new_password"

if they don't work try adding the -p option which will prompt you for the password.

---

### Post by kumakun on 2005-12-22
Success. The combination of swapping the hostnames in the /etc/hosts file and the other suggestions have worked. Now to create another user so I don't hose it up using root. Thanks, everyone.

---

### Post by saaz on 2006-03-29
[QUOTE=paddyg]First of all i think you should set a password for your MySQl root account:
```
mysqladmin -u root password "yourpassword"
```
Then start mysql as root
```
mysql -u root -p
```
Then grant privileges to users (for example, if you want another superuser):
```
GRANT ALL ON *.* TO youruser@localhost IDENTIFIED BY "youruserpassword";
```
[/QUOTE]

This worked for me:

First, assign passwords to both root accounts (localhost and your server's hostname):

```
shell> mysqladmin -u root password "newpwd"
shell> mysqladmin -u root -h host_name password "newpwd"
```

Then, login with:

```
shell>mysql -u root -p<password here with no space after the 'p'>
```

Finally, grant permission to both root accounts on everything:

```
mysql>GRANT ALL ON *.* TO root@localhost IDENTIFIED BY "root's password" WITH GRANT OPTION;
mysql>GRANT ALL ON *.* TO root@host_name IDENTIFIED BY "root's password" WITH GRANT OPTION;
```

---

### Post by TitanKing on 2006-09-11
```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'xxx.xxx.xxx.xxx' IDENTIFIED BY 'xxxxxxx' WITH GRANT OPTION;
```

Remember you need to create an account with your IP (xxx.xxx.xxx.xxx) as host, this tells MySQL that this user with this IP has permission to remotely access the Database.

---

