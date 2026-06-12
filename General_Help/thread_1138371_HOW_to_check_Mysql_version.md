---
title: "HOW to check Mysql version"
date: 2009-04-26
forum: General Help
---

### Post by runnner on 2009-04-26
There is a mysql database installed on the ubuntu server, I don't know how to check the mysql version info using the terminal window. Thanks for help!

---

### Post by spiderbatdad on 2009-04-26
i believe the command from the mysql prompt is ```
select version();
```
or 
```
mysql> SHOW VARIABLES LIKE "%version%";

```

---

### Post by mcduck on 2009-04-26
Or "apt-cache show mysql-server | grep Version" ;)

---

### Post by shahryar on 2012-02-22
The best article that explains the subject is [how to check MySQL version number]("http://www.geeksww.com/tutorials/database_management_systems/mysql/tips_and_tricks/how_to_check_mysql_version_number.php"). The article explains different methods of finding the version no. using different client programs.

go check it out.

---

