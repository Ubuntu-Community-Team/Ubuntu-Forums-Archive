---
title: "MySQL 4.1.12 and JDBC"
date: 2005-11-09
forum: Desktop Environments
---

### Post by mwiseley on 2005-11-09
This isn't a question. Since I didn't find my answer here, I thought I'd post it for the next guy...

The MySQL version 4.1.12 available in the Ubuntu "universe" has a serious problem with JDBC (access from Java applications). I'm using version 3.1.6 of the  Connector/J JDBC driver and Sun's Java 1.5.0.

The only info I was able to find regarding this behavior is here: [http://bugs.mysql.com/bug.php?id=12150]("http://bugs.mysql.com/bug.php?id=12150")

Problem: use of the PreparedStatement object is affected (it corrupts data on updates and creates bizarre nonsense data on inserts). Using "execute" on straight SQL statements did work - only PreparedStatements seemed to have a problem. The mysql client worked fine.

My fix was to uninstall the 4.1.12 server using Synaptic and manually install the 4.1.15 binary from mysql.com. My code now works as well as it did on RHEL.

Cheers,
Matt

---

### Post by jvictor on 2005-11-09
Thanks for the warning :)

---

### Post by tracer on 2005-11-11
[QUOTE=mwiseley]This isn't a question. Since I didn't find my answer here, I thought I'd post it for the next guy...

The MySQL version 4.1.12 available in the Ubuntu "universe" has a serious problem with JDBC (access from Java applications). I'm using version 3.1.6 of the  Connector/J JDBC driver and Sun's Java 1.5.0.
[/QUOTE]

I had the same problem.  It basically makes mysql useless if you code uses prepared statements (not uncommon).

I found a related mysql bug here: 

[http://bugs.mysql.com/bug.php?id=9777](http://bugs.mysql.com/bug.php?id=9777)

The standalone test program included causes the failure.

I'm hoping an updated Ubuntu package will be released soon.  In the meantime, setting the following JDBC property works around the issue:

```

useServerPrepStmts=false

```

---

### Post by jerrek71 on 2005-11-22
[QUOTE=tracer]
I'm hoping an updated Ubuntu package will be released soon.  In the meantime, setting the following JDBC property works around the issue:

```

useServerPrepStmts=false

```[/QUOTE]

Oh my, you guys have just saved me from getting REALLY stressed (I'm only mildly stressed). I wish I'd have thought to look here 3 hours ago - I've been trying to pin this little bug down since I just now switched from FC4 to Ubuntu and suddenly my JBoss app stopped working!

In case anyone needs it, JBoss 4 datasources can have the following parameter added;

```

<connection-property name="useServerPrepStmts">false</connection-property>

```

Which does what tracer said :)

These forums are absolutely the best resource on the net - every single Ubuntu (and sometimes general linux question) I've had has been answered here!! Good on you guys, keep up the fantastic work.

---

### Post by fajpunk on 2006-01-31
Hi everyone,

I too have run into this problem of not being able to use JDBC prepared statements with this version of MySQL and it's libraries.  I have some java code that uses prepared statements directly, and I was wondering if it would be possible to use another version of MySQL.

PHP5, Apache2, and MySQL were all installed using Synaptic.  So, using Synaptic, I uninstalled everything having to do with MySQL, including php5-mysql.  I then downloaded the binary version of MySQL 5 from the mysql website. 

The problem is, of course, I can't use it from php, unless I install mysql support.  The only way I know how to do this is through Synaptic, which installs a couple of other things, including libmysqlclient12, and mysql-common.  With libmysqlclient12, I am getting this error when I try to use mysql_connect from a php script: 

#1251 - Client does not support authentication protocol requested by server; consider upgrading MySQL client

As far as I can tell, this can't be done through synaptic.

My question is, is there any way I can my own installation of MySQL 5 without having to compile or manually install my own versions of PHP5 and Apache2?

Thanks!
Dan

---

