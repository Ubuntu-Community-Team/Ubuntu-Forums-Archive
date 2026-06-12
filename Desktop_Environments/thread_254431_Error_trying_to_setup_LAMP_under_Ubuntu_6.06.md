---
title: "Error trying to setup LAMP under Ubuntu 6.06"
date: 2006-09-09
forum: Desktop Environments
---

### Post by johnusa on 2006-09-09
I am new to Linux.  I am trying to setup LAMP.  Apache 2.2.3 seems to be working okay (which I installed from source via configure, make and make install).  I also downloaded Php 5.1.6.
When I issued the following command:

```
./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql
```


the last lines of the messages on my terminal were:

```
checking for MySQL support... yes
checking for specified location of the MySQL UNIX socket... no
checking for MySQL UNIX socket location... /var/run/mysqld/mysqld.sock
configure: error: Cannot find MySQL header files under yes.
Note that the MySQL client library is not bundled anymore!

```

I don't know what is wrong but anyone with sufficient knowledge to help will probably know what I need to do.

All suggestions are welcomed and thanks in advance for your help!

---

### Post by mssever on 2006-09-10
I gather that the configure error you're getting is from PHP?

Is there a particular reason you aren't using the repositories? Do you really need the latest versions of Apache and PHP? The reason I ask is that every time I've tried compiling PHP it's been an extremely frustrating experience that took a whole lot of time to solve. An I don't remember what I wound up doing. So, I would suggest that you stick to the repository versions unless you really do need the latest versions.

---

### Post by Thomas_ on 2006-09-17
I had the same problem, just install libmysqlclient15-dev

---

