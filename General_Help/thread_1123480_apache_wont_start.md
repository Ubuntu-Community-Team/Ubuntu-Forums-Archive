---
title: "apache wont start"
date: 2009-04-12
forum: General Help
---

### Post by hymns on 2009-04-12
hi,

i've problem here. it happen yesterday night. my notebook hanging and it back to normal after a few minute but it quite slow. then i decide to restart my laptop. after restart my localhost cant be access. the i try to check either apache run or not.

netstat -plant
-----------------------------------------------
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:55555         0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp        0      0 192.168.182.1:3990      0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:8888            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      -               
tcp        0      0 192.168.1.102:60613     140.211.166.3:8001      ESTABLISHED 10906/xchat     
tcp6       0      0 :::21                   :::*                    LISTEN      -  


sudo /etc/init.d/apache2 restart
----------------------------------------
 * Restarting web server apache2                                                           [ OK ] 


cat /var/log/apache2/error.log
----------------------------------------
[Sat Apr 11 23:36:45 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sat Apr 11 23:36:47 2009] [notice] Graceful restart requested, doing restart
[Sat Apr 11 23:36:47 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Apr 11 23:36:47 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sat Apr 11 23:36:48 2009] [notice] Graceful restart requested, doing restart
[Sat Apr 11 23:36:48 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Apr 11 23:36:52 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Apr 11 23:37:11 2009] [notice] Graceful restart requested, doing restart
[Sat Apr 11 23:37:11 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Apr 11 23:37:11 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Apr 11 23:37:53 2009] [notice] Graceful restart requested, doing restart
[Sat Apr 11 23:37:53 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Apr 11 23:37:53 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Apr 11 23:38:00 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Sat Apr 11 23:38:00 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sat Apr 11 23:38:10 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Apr 11 23:42:08 2009] [notice] caught SIGTERM, shutting down
[Sat Apr 11 23:42:42 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 12 10:53:08 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Sun Apr 12 10:53:08 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sun Apr 12 20:39:26 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 12 21:01:27 2009] [notice] Graceful restart requested, doing restart
[Sun Apr 12 21:01:27 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Apr 12 21:01:30 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 12 21:02:16 2009] [notice] SIGHUP received.  Attempting to restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Apr 12 21:02:16 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 12 21:02:25 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Sun Apr 12 21:02:25 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sun Apr 12 21:10:02 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 12 21:10:12 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Sun Apr 12 21:10:12 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sun Apr 12 21:10:22 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations


I try remove & install back LAMP but it still same problem. How to solve this problem? 

Thanks

---

### Post by paradigm2 on 2009-04-12
> **hymns said:**
> hi,

i've problem here. it happen yesterday night. my notebook hanging and it back to normal after a few minute but it quite slow. then i decide to restart my laptop. after restart my localhost cant be access. the i try to check either apache run or not.

netstat -plant
-----------------------------------------------
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:55555         0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp        0      0 192.168.182.1:3990      0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:8888            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      -               
tcp        0      0 192.168.1.102:60613     140.211.166.3:8001      ESTABLISHED 10906/xchat     
tcp6       0      0 :::21                   :::*                    LISTEN      -  


sudo /etc/init.d/apache2 restart
----------------------------------------
 * Restarting web server apache2                                                           [ OK ] 


cat /var/log/apache2/error.log
----------------------------------------
[Sat Apr 11 23:36:45 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sat Apr 11 23:36:47 2009] [notice] Graceful restart requested, doing restart
[Sat Apr 11 23:36:47 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Apr 11 23:36:47 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sat Apr 11 23:36:48 2009] [notice] Graceful restart requested, doing restart
[Sat Apr 11 23:36:48 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Apr 11 23:36:52 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Apr 11 23:37:11 2009] [notice] Graceful restart requested, doing restart
[Sat Apr 11 23:37:11 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Apr 11 23:37:11 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Apr 11 23:37:53 2009] [notice] Graceful restart requested, doing restart
[Sat Apr 11 23:37:53 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Apr 11 23:37:53 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Apr 11 23:38:00 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Sat Apr 11 23:38:00 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sat Apr 11 23:38:10 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Apr 11 23:42:08 2009] [notice] caught SIGTERM, shutting down
[Sat Apr 11 23:42:42 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 12 10:53:08 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Sun Apr 12 10:53:08 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sun Apr 12 20:39:26 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 12 21:01:27 2009] [notice] Graceful restart requested, doing restart
[Sun Apr 12 21:01:27 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Apr 12 21:01:30 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 12 21:02:16 2009] [notice] SIGHUP received.  Attempting to restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Apr 12 21:02:16 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 12 21:02:25 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Sun Apr 12 21:02:25 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sun Apr 12 21:10:02 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 12 21:10:12 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Sun Apr 12 21:10:12 2009] [notice] caught SIGWINCH, shutting down gracefully
[Sun Apr 12 21:10:22 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations


I try remove & install back LAMP but it still same problem. How to solve this problem? 

Thanks

Hmm.  No one else replied to this so I will chime in with something that I see wrong.

> 
127.0.1.1


It should NOT be using that.  This is probably why when you go to localhost even when it is running you are not seeing it.  It is set to use the wrong address.  Locally it should be 127.0.0.1.

I believe you might fix this in httpd.conf or apache.conf?

---

### Post by hymns on 2009-04-12
hi,

thank for reply. i've already change to 127.0.0.1 before this. but i leave back to default. still same. checking port, attemp open by lynx but still same. this my first time happen handling lamp. there anyone out there can help me?

thanks

---

### Post by Iowan on 2009-04-12
What is in your */etc/hosts* file?

---

### Post by hymns on 2009-04-13
> **Iowan said:**
> What is in your */etc/hosts* file?

127.0.0.1 localhost
127.0.1.1 machine-laptop

and other ipv6 below

---

### Post by Iowan on 2009-04-14
Can you **ping** localhost from the server? 
Can you **ping** 127.0.0.1 or 127.0.1.1? (Both *should* work.)

If not, check */etc/network/interfaces* to insure that it has (at least) ```
auto lo
iface lo inet loopback
```

[Another ]("http://ubuntuforums.org/showpost.php?p=5678856&postcount=10") post that might help with that "Could not reliably determine..." warning.

---

### Post by hymns on 2009-05-12
problem solve. remove virtualbox and it back to normal

---

