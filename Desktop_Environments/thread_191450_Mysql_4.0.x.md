---
title: "Mysql 4.0.x"
date: 2006-06-07
forum: Desktop Environments
---

### Post by lucianodenti on 2006-06-07
I need to install mysql v. 4.0.x on Dapper (i don't need v. 4.1 or v. 5.0) but i can't find a .deb package of this version.
Where Can I find a repository with an old mysql version ?

---

### Post by Ramses de Norre on 2006-06-07
Try the breezy repos, don't know whether the package needs older libs though. [Breezy mysql]("http://packages.ubuntu.com/breezy/misc/mysql-server")

---

### Post by adamkane on 2006-06-09
Pick one of these:

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

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

