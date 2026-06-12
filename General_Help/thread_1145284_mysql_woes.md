---
title: "mysql woes"
date: 2009-05-01
forum: General Help
---

### Post by Wonslung on 2009-05-01
hello....a friend of mine new to ubuntu tried to change his root mysql password using phpmyadmin.  I'm not sure EXACTLY what he did but i've tried everything to reset it, but no luck, we can't seem to fix it.

i've tried this method i've seed all over google:

   1. Stop the mysqld daemon process.
   2. Start the mysqld daemon process with the --skip-grant-tables option.
   3. Start the mysql client with the -u root option.
   4. Execute the UPDATE mysql.user SET Password=PASSWORD('password') WHERE User='root';
   5. Execute the FLUSH PRIVILEGES; command. 

i've tried about 10 variations of the above...
i've tried deleting mysql completely and reinstalling it.

I've tried PURGING it...no matter what, i can't seem to log in as root...even when setting it up as root everything seemed to go smoothly, it asked me for the root password and everything, i set it, but still no love.

does anyone have a surefire way to reset the mysql root password in ubuntu.

(i think it's something to do with there being more than one "root" user in mysql..., on my personal machine i have 3 "root" places where i can change the password in phpmyadmin, so i'm guessing he originally changed the wrong one and now it's not letting us log in from localhost)

i'm at my wits end...i can't believe the purge/reinstall didn't work...especially since it asked me for the password

---

### Post by cmnorton on 2009-05-01
Have you seen this?

[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix)

---

### Post by Wonslung on 2009-05-03
yeah, i saw that.

i was finally able to get what i needed done by removing /var/lib/mysql then purging the mysql-server install

---

