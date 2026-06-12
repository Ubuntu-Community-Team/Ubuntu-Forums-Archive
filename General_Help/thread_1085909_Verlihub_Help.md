---
title: "Verlihub Help"
date: 2009-03-03
forum: General Help
---

### Post by bmwracer0 on 2009-03-03
Hi, I installed verlihub from the .deb, and am trying to install the plugins. I downloaded them, and during a ./configure, encountered a problem with the configuration. Per the launchpad solution, I edited the verlihub_config file, and configuration succeeded. However, during make, I have the following error:

```
In file included from /usr/include/verlihub/cconfmysql.h:24,
                 from ciplog.h:25,
                 from cpiiplog.h:29,
                 from cpiiplog.cpp:21:
/usr/include/verlihub/cmysql.h:18:19: error: mysql.h: No such file or directory
In file included from /usr/include/verlihub/cconfmysql.h:24,
                 from ciplog.h:25,
                 from cpiiplog.h:29,
                 from cpiiplog.cpp:21:
/usr/include/verlihub/cmysql.h:44: error: expected ';' before '*' token
In file included from /usr/include/verlihub/cconfmysql.h:25,
                 from ciplog.h:25,
                 from cpiiplog.h:29,
                 from cpiiplog.cpp:21:
/usr/include/verlihub/cquery.h:40: error: 'MYSQL_ROW' does not name a type
/usr/include/verlihub/cquery.h:49: error: expected ';' before '*' token
In file included from ciplog.h:25,
                 from cpiiplog.h:29,
                 from cpiiplog.cpp:21:
/usr/include/verlihub/cconfmysql.h:65: error: expected ',' or '...' before '&' token
/usr/include/verlihub/cconfmysql.h:171: error: 'MYSQL_ROW' does not name a type
/usr/include/verlihub/cconfmysql.h:173: error: expected `)' before 'row'
/usr/include/verlihub/cconfmysql.h: In member function 'void nConfig::cConfMySQL::ufLoad::operator()(nConfig::cConfigItemBase*)':
/usr/include/verlihub/cconfmysql.h:177: error: 'mRow' was not declared in this scope

```
Any ideas?
Thanks!

---

