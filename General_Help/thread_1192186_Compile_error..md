---
title: "Compile error."
date: 2009-06-19
forum: General Help
---

### Post by DedicatedOT on 2009-06-19
```


root@vps:/sources/OTServ/0.2.3# make
g++ -I. -I/usr/include/libxml2 -I/usr/include/lua5.1 -Werror -Wall -O1 -D_THREAD_SAFE -D_REENTRANT -D__NO_HOMEDIR_CONF__ -D__USE_MYSQL__ -D__USE_SQLITE__ -c actions.cpp
In file included from iologindata.h:27,
                 from game.h:37,
                 from actions.cpp:26:
database.h:31:25: error: mysql/mysql.h: No such file or directory
In file included from iologindata.h:27,
                 from game.h:37,
                 from actions.cpp:26:
database.h:126: error: 'MYSQL_ROW' has not been declared
make: *** [actions.o] Error 1

```

Hi, why I keep getting this error when compiling? I'm using mySQL.

---

### Post by credobyte on 2009-06-19
Have you installed *libmysqlclient15-dev* ?

---

### Post by DedicatedOT on 2009-06-19
I am not sure, how do I check? I am new to all of this. It's a Virtual Private server i rented. And I only executed the following lines so far using wget.
```

sudo apt-get install autoconf libtool libxml2-dev g++ libgmp3-dev libboost1.35-dev liblua5.1-0-dev
```

Help please.

---

### Post by DedicatedOT on 2009-06-19
And I know phpmyadmin is installed, but I do not know what directory it is in... Apache is installed as well.

---

