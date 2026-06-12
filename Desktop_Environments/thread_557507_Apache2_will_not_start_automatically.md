---
title: "Apache2 will not start automatically"
date: 2007-09-22
forum: Desktop Environments
---

### Post by mosestruong on 2007-09-22
I'm having problem with Apache2 not starting automatically.

When I tried to run start it manually
sudo /etc/init.d/apache2 start

There's no error messages, but apache2 still does not run. (The same goes for restart, reload, force-reload; however stop works)

However, if I run
sudo /usr/sbin/apache2

Apache2 will start without any problem.

I have apache2 (2.2.3-3.2ubuntu1 version installed). Would anyone know what might be the cause of this? Thanks.

---

### Post by diophantine_programmer on 2007-09-26
I searched on Google for "/etc/init.d/apache2 does not start" (without
quotes), and

   [http://www.mail-archive.com/debian-apache@lists.debian.org/msg09084.html](http://www.mail-archive.com/debian-apache@lists.debian.org/msg09084.html)

was one of the hits.  From that webpage:

```


adding set -x to /etc/init.d/apache2, I can see that /etc/default/apache2 
contains NO_START=1

Maybe there should be a warning message on /etc/init.d/apache2 whenever 
NO_START is set to 1 (or != 0) ?


```

On my system, I changed the /etc/default/apache2 file from "NO_START = 1"
to "NO_START = 0", and then /etc/init.d/apache2 worked.  YMMV, of course.


According to the followup to the above message,

  [http://www.mail-archive.com/debian-apache@lists.debian.org/msg09162.html](http://www.mail-archive.com/debian-apache@lists.debian.org/msg09162.html)

this is fixed in apache2 2.2.4-1  (But I have not confirmed this myself!)

HTH!

---

### Post by reduxtion on 2007-10-18
I currently am having the same problems. No errors, apache just won't start. apachectl doesn't even start Apache. This is a fresh upgrade from Feisty using do-release-upgrade.

---

