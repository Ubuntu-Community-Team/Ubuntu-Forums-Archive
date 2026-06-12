---
title: "Multiple Apache processes"
date: 2009-04-03
forum: General Help
---

### Post by Volt9000 on 2009-04-03
I just installed LAMP using sudo tasksel and now that it's done, I see there's multiple apache2 process running. Here's my output from ps ax | grep apache:

```

28350 ?        Ss     0:00 /usr/sbin/apache2 -k start
28449 ?        S      0:00 /usr/sbin/apache2 -k start
28450 ?        S      0:00 /usr/sbin/apache2 -k start
28451 ?        S      0:00 /usr/sbin/apache2 -k start
28453 ?        S      0:00 /usr/sbin/apache2 -k start
28455 ?        S      0:00 /usr/sbin/apache2 -k start
28634 ?        S      0:00 /usr/sbin/apache2 -k start

```

So I tried stopping it, with apache2ctl stop and /etc/init.d/apache2 stop but the processes are still running. What's going on here?

---

### Post by paradigm2 on 2009-04-03
> **Volt9000 said:**
> I just installed LAMP using sudo tasksel and now that it's done, I see there's multiple apache2 process running. Here's my output from ps ax | grep apache:

```

28350 ?        Ss     0:00 /usr/sbin/apache2 -k start
28449 ?        S      0:00 /usr/sbin/apache2 -k start
28450 ?        S      0:00 /usr/sbin/apache2 -k start
28451 ?        S      0:00 /usr/sbin/apache2 -k start
28453 ?        S      0:00 /usr/sbin/apache2 -k start
28455 ?        S      0:00 /usr/sbin/apache2 -k start
28634 ?        S      0:00 /usr/sbin/apache2 -k start

```

So I tried stopping it, with apache2ctl stop and /etc/init.d/apache2 stop but the processes are still running. What's going on here?

I believe this is typical of Apache.  It spawns multiple instances and keeps them on standby in order to quickly be able to handle requests.  It should be configurable in httpd.conf, probably /etc/httpd.conf, I believe.

---

### Post by Volt9000 on 2009-04-03
I see, so the processes are running but not actually "active"? 

Then why is it even when I stop the apache service I can still go to localhost and get the "It worked!" message?

---

### Post by paradigm2 on 2009-04-03
> **Volt9000 said:**
> I see, so the processes are running but not actually "active"? 

Then why is it even when I stop the apache service I can still go to localhost and get the "It worked!" message?


Hmm.  I only have a ltitle experience with this. Well if you kill -9 each individual process they would just be respawned by the parent apache process.  But /etc/init.d/apache2 stop ought to do the trick, I'd think.... unless:

1. Something else is watching apache to make sure it is running.

2. I have had a (production webserver) machine before where there were separate apache servers running.  It's possible.

What is:

```

less /var/log/apache2/error.log

```

Showing you?

Usually it will have status messages such as:

```

[Fri Apr 03 19:26:56 2009] [notice] caught SIGTERM, shutting down
[Fri Apr 03 19:28:07 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4 with Suhosin-Patch configured -- resuming normal operations

```

---

### Post by paradigm2 on 2009-04-03
Here.  To sort fo see why you have all these apache processes, have a look at:

```

less /etc/apache2/apache2.conf

```

This general area:

```

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare

```

This should explain a bit what is happening.  It is normal for there to be multiple processes.

Minspareservers tells it to always keep at elast an extra five.  Maxspareservers says to keep no more than 10.  And there may be up to 150 apache processes running!

---

### Post by Volt9000 on 2009-04-03
Here's my error.log file:

```

[Fri Apr 03 21:29:56 2009] [notice] Apache/2.2.9 (Ubuntu) configured -- resuming normal operations
[Fri Apr 03 21:29:57 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Apr 03 21:29:57 2009] [notice] Apache/2.2.9 (Ubuntu) configured -- resuming normal operations
[Fri Apr 03 21:33:43 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Apr 03 21:33:46 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico

```

Ok, so I manually terminated all apache processes, and then suddenly realized why I couldn't do it before: I forgot to precede my commands with sudo! Once I did that Apache terminated properly and all processes were gone.
When I restarted it I got the same number of processes again.

> **paradigm2 said:**
> Here.  To sort fo see why you have all these apache processes, have a look at:

```

less /etc/apache2/apache2.conf

```

This general area:

```

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare

```

This should explain a bit what is happening.  It is normal for there to be multiple processes.

Minspareservers tells it to always keep at elast an extra five.  Maxspareservers says to keep no more than 10.  And there may be up to 150 apache processes running!

Great, thanks! :D

---

