---
title: "logcheck error"
date: 2006-01-18
forum: General Help
---

### Post by mochafrap on 2006-01-18
Folks!

I get this error on the report emailed to me:

Warning: If you are seeing this message, your log files may not have been
checked!

Details:
Failed to get lockfile: /var/lock/logcheck/logcheck.lock

Check temporary directory:

there is no logcheck.lock file present there
also already chown -R logcheck /var/lock/logcheck/
with no change...playing around permissions no change

am trying to configure this with syslog-ng
as described here:

[http://www.debian-administration.org/articles/278](http://www.debian-administration.org/articles/278)

any ideas? Google only lead me to an old email on a Debian list but no
solution obtained

 :( 

thanks in advance

---

