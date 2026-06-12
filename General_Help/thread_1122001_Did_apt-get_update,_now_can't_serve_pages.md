---
title: "Did apt-get update, now can't serve pages"
date: 2009-04-10
forum: General Help
---

### Post by jsdegard on 2009-04-10
Hello

Earlier today I did an apt-get update command to meet a dependency to install cups-pdf.  Now, I can't get serve pages.  When I try to restart apache, I get the error:

jsdegard@lambda:/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
httpd (no pid file) not running
   ...done.

I did a search and could not find an httpd.pid file, if that is what I need.  Any suggestions?

Ubuntu 8.04

Thanks

Jeremy

---

### Post by pavel989 on 2009-04-10
well u can just save ur htdocs and reinstall, or find out where the pid file should be (ur httpd.conf file should tell u) and just make the file there.

---

### Post by jsdegard on 2009-04-10
Well, my htttpd.conf file just says this:

BrowserMatch ^Mozilla/4 gzip-only-text/html
BrowserMatch ^Mozilla/4\.0[678] no-gzip
BrowserMatch \bMSIE !no-gzip !gzip-only-text/html

I thought I might see something here that would help:

jsdegard@lambda:/$ apache2 -V
Server version: Apache/2.2.8 (Ubuntu)
Server built:   Jun 25 2008 13:54:13
Server's Module Magic Number: 20051115:11
Server loaded:  APR 1.2.11, APR-Util 1.2.12
Compiled using: APR 1.2.11, APR-Util 1.2.12
Architecture:   32-bit
Server MPM:     Prefork
  threaded:     no
    forked:     yes (variable process count)
Server compiled with....
 -D APACHE_MPM_DIR="server/mpm/prefork"
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D APR_USE_PTHREAD_SERIALIZE
 -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D DYNAMIC_MODULE_LIMIT=128
 -D HTTPD_ROOT=""
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
 -D DEFAULT_LOCKFILE="/var/run/apache2/accept.lock"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="/etc/apache2/mime.types"
 -D SERVER_CONFIG_FILE="/etc/apache2/apache2.conf"

The fact that HTTPD ROOT is blank seems suspect, and I still don't know where my pid file is.  Anything else?

Thanks

Jeremy

---

### Post by jsdegard on 2009-04-10
I can't find anything in the ifconfifg either.

jsdegard@lambda:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:34:a0:e5
          inet addr:192.168.30.30  Bcast:192.168.30.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe34:a0e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12108219 (11.5 MB)  TX bytes:24485008 (23.3 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

Please help!

Jeremy

---

### Post by pavel989 on 2009-04-10
does "/var/run/apache2.pid" exsist?

---

### Post by jsdegard on 2009-04-17
Ok, I figured this out.  When I ran the update command, it must have updated something that no longer supports eAccelerator.  Sooo, I had to comment that out of the /etc/php5/apache2/php.ini file, restart apache, and bingo.  I don't think I was getting alot of bang out of eAccelerator anyway.

Thanks for trying to help

---

### Post by demifamm7 on 2011-01-14
> **jsdegard said:**
> HelloEarlier today I did an apt-get update command to meet a dependency to install cups-pdf. Now, I can't get serve pages. When I try to restart apache, I get the error:jsdegard@lambda:/[[COLOR=#000000]etc/apache2[/COLOR]](http://www.sharit.biz/bg/travel-and-tourism/the-professional-most-excellent-directives-in.html)$ sudo /etc/init.d/apache2 restart* Restarting web server apache2httpd (no pid file) not running...done.I did a search and could not find an httpd.pid file, if that is what I need. Any suggestions?Ubuntu 8.04ThanksJeremyI encountered the same problem, Could you give more details? It failed to solve my problem.

---

