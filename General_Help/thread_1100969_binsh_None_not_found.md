---
title: "/bin/sh: None: not found"
date: 2009-03-19
forum: General Help
---

### Post by map7 on 2009-03-19
I've noticed that I'm getting a lot of system mail which includes the error:

```
From: [email]root@ws10.lan[/email] (Cron Daemon)
To: [email]map7@####.lan[/email]
Subject: Cron <map7@####> None
Content-Type: text/plain; charset=UTF-8
Date: Fri, 20 Mar 2009 10:47:01 +1100

/bin/sh: None: not found
```

This is happening every minute.  I've checked my cron but there doesn't seem to be anything which could be failing.  Here is my /etc/crontab file:


```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


# Backup projects to the server paistram
* 5     * * *   root    /home/map7/bin/backup_projects
```

---

### Post by cariboo on 2009-03-19
have you looked in /bin to see if sh is there. To do it the gui way bot to Places-->Home Folder-->Filesystem-->bin

Jim

---

### Post by kerry_s on 2009-03-19
> * 5     * * *   root    /home/map7/bin/backup_projects

send that to a log:

* 5     * * *   root    /home/map7/bin/backup_projects >> /path/where/you/want

---

### Post by Nano_ext3 on 2009-03-19
Not sure if this will help, but I know #!/bin/bash of course available in that directory but maybe you have to install the C Shell?  This has the sh* prompt like so:

mikeyd@mikeyd-laptop:~$ csh
% 


```
apt-get install csh

```

My apologies if this is not what you were looking for.

-Nano

---

### Post by kerry_s on 2009-03-19
> **Nano_ext3 said:**
> Not sure if this will help, but I know #!/bin/bash of course available in that directory but maybe you have to install the C Shell?  This has the sh* prompt like so:

mikeyd@mikeyd-laptop:~$ csh
% 


```
apt-get install csh

```

My apologies if this is not what you were looking for.

-Nano

:lolflag: in ubuntu "sh" is linked to "dash".
the error is because he didn't out put to a log.> man crontab

---

### Post by Nano_ext3 on 2009-03-19
My bad, sorry, everyday I learn something new, thats why I love linux :)

Thanks though,

_Nano

---

