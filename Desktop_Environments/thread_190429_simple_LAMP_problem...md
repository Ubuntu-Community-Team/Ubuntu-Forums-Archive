---
title: "simple LAMP problem.."
date: 2006-06-06
forum: Desktop Environments
---

### Post by i++ on 2006-06-06
hi, im trying to set up a simple lamp server on a machine i have at home, running 6.06.

```
server@server-desktop:/usr$ sudo mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

i need to create a user and set the root password yet am not sure how to do so. sorry if this is the wrong section to place this issue.

im following this [HTML]https://wiki.ubuntu.com/ApacheMySQLPHP[/HTML]

any help would be brilliant :D 

thanks, i++

---

### Post by Ramses de Norre on 2006-06-06
Try it without sudo (just a wild guess, maybe it works).

---

### Post by i++ on 2006-06-06
no luck im afraid :( thanks anyway!

---

### Post by hardclip on 2006-06-06
Hi,

The SQL root password is blank or empty by default. 

Try:

server@server-desktop:/usr$ sudo mysql -u root -p

This will prompt you for the root password. Just press return and you are in. Use SQL commands to change password from there.

Ed...

---

### Post by i++ on 2006-06-06
thanks for the reply. when i tried that it asked me for a password,i just left it blank and hit enter, but it didnt log me in to the mysql console

server@server-desktop:/usr$ sudo mysql -u root -p
Password:
server@server-desktop:/usr$

any idea's?

---

### Post by drfalkor on 2006-06-07
type you'r sudo password, then enter, and then enter again ?

---

### Post by adamkane on 2006-06-07
Make your life easier, and use phpmyadmin.

Install one of these:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Then open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

Find or add a new database. Go to Permissions to add users.

---

### Post by Geekboy on 2006-06-22
I just had this same problem.  I opened [http://localhost/phpmyadmin]("http://localhost/phpmyadmin") and was able to log on as root and use my sudo password.

---

### Post by ohgod on 2006-06-23
"MySql Administrator" is nice too.  Not sure what the package is called, but I'm sure you can search for it with apt-get (Synaptic, etc).

[QUOTE=adamkane]Make your life easier, and use phpmyadmin.

Install one of these:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Then open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

Find or add a new database. Go to Permissions to add users.[/QUOTE]

---

