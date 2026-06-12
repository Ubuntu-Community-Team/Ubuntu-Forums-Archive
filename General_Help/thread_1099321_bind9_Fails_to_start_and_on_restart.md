---
title: "bind9 Fails to start and on restart"
date: 2009-03-18
forum: General Help
---

### Post by sswittch on 2009-03-18
Hi I have just installed a fresh copy of ubuntu 8.10 - which worked seemlessly and then ISPconfig - I am now having a problem with bind9 failing on boot and am unsure how to fix this problem, here is a snippet of my syslog

```
root@server1:/# /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                        rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [fail]
 * Starting domain name service... bind9                                 [fail]
```

syslog
```
Mar 18 16:31:09 server1 named[9076]: starting BIND 9.5.0-P2 -u bind -t /var/lib/named
Mar 18 16:31:09 server1 named[9076]: found 1 CPU, using 1 worker thread
Mar 18 16:31:09 server1 named[9076]: loading configuration from '/etc/bind/named.conf'
Mar 18 16:31:09 server1 kernel: [ 4142.827487] type=1503 audit(1237357869.526:20): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid$
Mar 18 16:31:09 server1 named[9076]: none:0: open: /etc/bind/named.conf: permission denied
Mar 18 16:31:09 server1 named[9076]: loading configuration: permission denied
Mar 18 16:31:09 server1 named[9076]: exiting (due to fatal error)
```

Any help would be greatly appreciated.

---

### Post by ruel- on 2009-03-18
try chmod or chown..

---

### Post by sswittch on 2009-03-18
> **ruel- said:**
> try chmod or chown..

```
root@server1:/# chmod 666 /var/lib/named/dev/null /var/lib/named/dev/random
root@server1:/# chown -R bind:bind /var/lib/named/var/*
root@server1:/# chown -R bind:bind /var/lib/named/etc/bind
root@server1:/# /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                        rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [fail]
 * Starting domain name service... bind9                                 [fail]

```

still no joy :(

---

### Post by ruel- on 2009-03-18
ok, I found a possible fix:

[http://www.howtoforge.org/forums/showthread.php?p=116893](http://www.howtoforge.org/forums/showthread.php?p=116893)

---

### Post by sswittch on 2009-03-18
> **ruel- said:**
> ok, I found a possible fix:

[http://www.howtoforge.org/forums/showthread.php?p=116893](http://www.howtoforge.org/forums/showthread.php?p=116893)

hey, thanks.

That didn't quite fix it for me but pointed me in the right direction for where the error was.

I removed the offending mail filter application

```
/etc/init.d/apparmor stop
update-rc.d -f apparmor remove
apt-get remove apparmor apparmor-utils
```

---

