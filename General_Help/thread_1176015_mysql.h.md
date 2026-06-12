---
title: "mysql.h"
date: 2009-06-01
forum: General Help
---

### Post by bigmb on 2009-06-01
Ok. I have just installed mysql including the libmysqlclient package (probably not perfect syntax there, but that's ok...)

I have a very simple c program I am trying to run that requires the mysql.h library.

mysql_config --cflags returns:
-I/usr/include/mysql

So I try to make a simple compilation with:

gcc testing.c -o testing.bin -I/usr/include/mysql -L/usr/local/mysql/lib -lmysclient -lz

I get this error:

/usr/bin/ld: cannot find -lmysclient
collect2: ld returned 1 exit status

How would I go about correcting this? Am I still missing something I need to install? (turns out mysql.h was not included in the original mysql package I installed)

Thanks.

---

