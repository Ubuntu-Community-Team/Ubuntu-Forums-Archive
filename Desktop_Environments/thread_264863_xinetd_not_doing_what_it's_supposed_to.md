---
title: "xinetd not doing what it's supposed to"
date: 2006-09-25
forum: Desktop Environments
---

### Post by hypermegachi on 2006-09-25
xinetd is not working at all.

here's the tail of syslog:
```

Sep 25 09:29:31 hostname xinetd[23166]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Sep 25 09:29:31 hostname  xinetd[23166]: Started working: 2 available services

```

and here's svn:
```

service svn
{
        port = 3690
        socket_type = stream
        protocol = tcp
        wait = no
        user = www-data
        server = /usr/bin/svnserve
        server_args = -i -r /server/repos
        disable = no
}

```

and here's vsftp:
```

service ftp
{
        disable = no
        socket_type = stream
        wait = no
        user = root
        flags = SENSOR
        server = /usr/sbin/vsftpd
        deny_time = 120
}

```

i'm unable to access either service.  what should i look for?  thanks.

---

### Post by hypermegachi on 2006-09-25
btw, listen=NO is set in vsftpd.conf

---

