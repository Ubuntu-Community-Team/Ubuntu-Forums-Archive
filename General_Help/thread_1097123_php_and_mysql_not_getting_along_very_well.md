---
title: "php and mysql not getting along very well"
date: 2009-03-15
forum: General Help
---

### Post by shortridge11 on 2009-03-15
I installed php5 and mysql and php5-mysql, apache2 is up and running, etc.
I logged into mysql and created a user called netjukeuser, and then logged in with him and created a database called netjuke.

Then i used the php installer for netjuke 
[http://sourceforge.net/projects/netjuke](http://sourceforge.net/projects/netjuke)

It uses a php installer script to use the database and user you created to make some tables.  Somehow, after it creates about 8 tables it fails while creating a table.  It doesn't really give a descriptive message, and i was wondering if there was some type of log i could check.  Or if anyone knows anything about netjuke, i'd also be satisfied.

Thanks

---

### Post by LoneWolfJack on 2009-03-16
this should be a good starting point:
[http://dev.mysql.com/doc/refman/5.1/en/log-files.html]("http://dev.mysql.com/doc/refman/5.1/en/log-files.html")

---

