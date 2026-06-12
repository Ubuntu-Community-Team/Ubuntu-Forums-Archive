---
title: "sockets error"
date: 2006-02-13
forum: Desktop Environments
---

### Post by dabear on 2006-02-13
When I start amsn, I get this error before the program exits: «Unable to get  a socket from localhost. Check your /etc/hosts file, please». I also get some sockets error when trying to restart mysql:
```

bjorninge@ubuntuBreezy:~$ sudo /etc/init.d/mysql restart
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
bjorninge@ubuntuBreezy:~$

```
How do I fix this?

(kubuntu breezy btw)

---

### Post by pedrowing on 2006-02-20
i got the same error on amsn, looks like it has something to do with my disabled ipv6, anyone have any idea?

my /etc/hosts:


127.0.0.1       localhost.localdomain   localhost       ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by dabear on 2006-02-21
I fund out that the reason- at least for me- was that I had terminated the network at boot, but using gtkwifi I could still use the internet, just not mysql and amsn (gaim worked)

---

