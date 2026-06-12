---
title: "Help with sqlplus in Ubuntu"
date: 2009-06-22
forum: General Help
---

### Post by oakdeveloper on 2009-06-22
Hi,

I've installed Oracle XE on my Ubuntu 9.04. I'm unable to connect to Oracle XE from the command line using sqlplus. When I type the command it gives me an error saying that the command is not found though I can see the man page for sqlplus. Should I install any other packgage for getting the command line sqlplus ? Please help me. I'm new to working with Oracle on a linux machine.

Regards,
Babu

---

### Post by Waappu on 2009-06-22
Hi

You need set enviroment variables.

Edit your .bashrc file
```
nano ~/.bashrc
```
include the lines at end of file:
```

ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME
export ORACLE_SID=XE

export PATH

```
Logout and back in so change affect

See also this guide
[https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)

---

### Post by NetJunky on 2009-09-11
Hi. I'm trying to install just **SQL*Plus**. Read this article [COLOR=Blue][http://samushka.blogspot.com/2009/04/installing-oracle-sqlplus-in-ubuntu.html](http://samushka.blogspot.com/2009/04/installing-oracle-sqlplus-in-ubuntu.html)[/COLOR]

Did everything there written, but I still get this error.
Do not know how to make it right.

Can anyone help?

```
sqlplus: error while loading shared libraries: libsqlplus.so: cannot open shared object file: No such file or directory
```

-------------------------------------------------

Ok. I stoped waiting and did everything, that was written in post above. Also read the link given below. Now can use Oracle XE and it SQL*Plus.

---

