---
title: "cleaning up you /var/log folder..."
date: 2009-01-01
forum: General Help
---

### Post by kforum on 2009-01-01
ok for some strange reason now my log files have taken 15gb of space, it seems that happened after i tried downloading an iso(xubuntu 8.10 to be exact), now i dont know why... but regardless of it, my question is:
is there any general method to delete those log files, or can i just sudo into the folder and manually pick teh ones that now are over 5gb in size and erase them?

also, is there any cleaner tool of sorts for lin out there?

thanks in advance for any response.

cheers

:P

---

### Post by dcstar on 2009-01-01
> **kforum said:**
> ok for some strange reason now my log files have taken 15gb of space, it seems that happened after i tried downloading an iso(xubuntu 8.10 to be exact), now i dont know why... but regardless of it, my question is:
is there any general method to delete those log files, or can i just sudo into the folder and manually pick teh ones that now are over 5gb in size and erase them?

also, is there any cleaner tool of sorts for lin out there?


Install the **logrotate** package.

---

### Post by kforum on 2009-01-02
i have that, but thats the result i get:


logrotate 3.7.1 - Copyright (C) 1995-2001 Red Hat, Inc.
This may be freely redistributed under the terms of the GNU Public License

Usage: logrotate [-dfv?] [-d|--debug] [-f|--force] [-m|--mail=command]
        [-s|--state=statefile] [-v|--verbose] [-?|--help] [--usage]
        [OPTION...] <configfile>


so...

---

### Post by cdtech on 2009-01-02
Make sure you have a logrotate configuration file within /etc/logrotate.conf and try running:
```
/usr/sbin/logrotate -dv /etc/logrotate.conf
```

---

### Post by kforum on 2009-01-02
im i sleepy, or?

this is what happened:

:~$ /usr/sbin/logrotate –dv /etc/logrotate.conf
error: cannot stat –dv: No such file or directory
:~$

very strange

---

### Post by cdtech on 2009-01-02
Don't add that squiggly thing:
```
/usr/sbin/logrotate &#8211;dv /etc/logrotate.conf
```

---

### Post by kforum on 2009-01-03
thats part of the name:

name@pc:~$ /usr/sbin/logrotate –dv /etc/logrotate.conf
error: cannot stat –dv: No such file or directory
name@pc:~$ 


;)

---

### Post by cdtech on 2009-01-06
I'm sorry, I don't know why that showed as a single large line. That dash should be a single dash:
```
/usr/sbin/logrotate -dv /etc/logrotate.conf
```

Sorry for that........

---

### Post by mcduck on 2009-01-06
The log files should be automatically cleaned by default.

I'd suggest instead focusing on finding out what program/error caused your logs to grow that big..

---

### Post by DPic on 2009-11-20
is this a problem with a macbook? my friend just ran into this and upon googling i found it happens to others as well
[http://forums.macrumors.com/archive/index.php/t-641936.html](http://forums.macrumors.com/archive/index.php/t-641936.html)

anybody know if there's a bug report?

---

