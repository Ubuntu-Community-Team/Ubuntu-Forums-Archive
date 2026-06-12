---
title: "Problems with LAMP on localhost ..."
date: 2020-05-08
forum: Desktop Environments
---

### Post by dbee on 2020-05-08
I've set up Apache2, PHP and MySQL on ubuntu 18.0.4 but i'm having problems configuring it to work properly ...

Apache seems to be working 
```

service apache2 status

&#9679; apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2020-05-08 14:26:24 IST; 3min 5s ago
     Docs: https://httpd.apache.org/docs/2.4/
  Process: 14530 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCESS)
 Main PID: 14534 (apache2)
    Tasks: 6 (limit: 4915)
   Memory: 13.6M
   CGroup: /system.slice/apache2.service
           &#9500;&#9472;14534 /usr/sbin/apache2 -k start
           &#9500;&#9472;14535 /usr/sbin/apache2 -k start
           &#9500;&#9472;14536 /usr/sbin/apache2 -k start
           &#9500;&#9472;14537 /usr/sbin/apache2 -k start
           &#9500;&#9472;14538 /usr/sbin/apache2 -k start
           &#9492;&#9472;14539 /usr/sbin/apache2 -k start

May 08 14:26:24 dara-HP-Pavilion-Notebook-15-bc5xxx systemd[1]: Starting The Apache HTTP Server...
May 08 14:26:24 dara-HP-Pavilion-Notebook-15-bc5xxx apachectl[14530]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directi
May 08 14:26:24 dara-HP-Pavilion-Notebook-15-bc5xxx systemd[1]: Started The Apache HTTP Server.

```

mysqld is listening on port 3306, or at least something is listening on 3306. I have bind_address = 127.0.0.1 in the mysql conf file ...

```

ss -ln | grep 3306

dara@dara-HP-Pavilion-Notebook-15-bc5xxx:/var/log/apache2$ ss -ln | grep 3306
tcp                LISTEN              0                    128                                                                       127.0.0.1:3306                                                0.0.0.0:*                                   
tcp                LISTEN              0                    70                                                                                *:33060                                                     *:*                                   

```

I have the wordpress site enabled on apache ...

```

dara@dara-HP-Pavilion-Notebook-15-bc5xxx:/var/log/apache2$ sudo a2ensite mysite
Site mysite already enabled

```

The error log for apache2 shows nothing ... same for the access log

```

dara@dara-HP-Pavilion-Notebook-15-bc5xxx:/var/log/apache2$ tail error.log

[Fri May 08 12:26:06.911405 2020] [mpm_prefork:notice] [pid 935] AH00163: Apache/2.4.41 (Ubuntu) configured -- resuming normal operations
[Fri May 08 12:26:06.911448 2020] [core:notice] [pid 935] AH00094: Command line: '/usr/sbin/apache2'
[Fri May 08 14:26:24.225766 2020] [mpm_prefork:notice] [pid 935] AH00169: caught SIGTERM, shutting down
[Fri May 08 14:26:24.277930 2020] [mpm_prefork:notice] [pid 14534] AH00163: Apache/2.4.41 (Ubuntu) configured -- resuming normal operations
[Fri May 08 14:26:24.277965 2020] [core:notice] [pid 14534] AH00094: Command line: '/usr/sbin/apache2'

```

I know php is running because I can access the page localhost/wp-admin/install.php

```

Already Installed
You appear to have already installed WordPress. To reinstall please clear your old database tables first.

```

But the root index.php gives me 
```

This site can’t be reached localhost refused to connect.
Try:

Checking the connection
Checking the proxy and the firewall
ERR_CONNECTION_REFUSED

```

sort of running out of ideas ...

Thanks in advance

---

