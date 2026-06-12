---
title: "Ubuntu sipXpbx errors"
date: 2006-09-28
forum: Desktop Environments
---

### Post by upanda on 2006-09-28
Dear Gurus,
I have installed sipxpbx and em running into a couple of problems. First of all it requires "mod_access.so" which I don't have and 2nd it runs various bash scripts under the directory /var/run/sipxpbx, however I have no such directory nor those scripts. Pray help me.

```

user@sipx:~$ sudo /etc/init.d/sipxpbx start
Checking rpm configuration file updates:success

Checking apache:failure

Checking hostname:success

Checking /etc/hosts file:success

Checking ssl configuration:failure

Checking watchdog:failure

Checking sipproxy:failure

Checking sipxconfig:failure

Checking sipXvxml:failure

Checking sipxpark:failure

Checking sipxpresence:failure

Checking sipstatus:failure

Checking sipregistrar:failure

Checking sipauthproxy:failure

Checking keepalive:failure

sipXpbx:
sipXpbx: sipXpbx configuration problems found:
sipXpbx:
sipXpbx: Check apache
sipXpbx:    Syntax error on line 235 of /etc/sipxpbx/httpd.conf:
sipXpbx: module access_module is built-in and can't be loaded
sipXpbx:
sipXpbx: Check ssl configuration
sipXpbx:    SSL certificate name 'ubuntuserver.siinfobank.local' is not one of:
'sipx.siinfobank.local'
sipXpbx: SSL certificate: /etc/sipxpbx/ssl/ssl.crt
sipXpbx:
sipXpbx: Check watchdog
sipXpbx:    bash: /var/run/sipxpbx/watchdog.result: No such file or directory
sipXpbx: cat: /var/run/sipxpbx/watchdog.result: No such file or directory
sipXpbx:
sipXpbx: Check sipproxy
sipXpbx:    bash: /var/run/sipxpbx/sipproxy.result: No such file or directory
sipXpbx: cat: /var/run/sipxpbx/sipproxy.result: No such file or directory
sipXpbx:
sipXpbx: Check sipxconfig
sipXpbx:    psql: FATAL:  Ident authentication failed for user "postgres"
sipXpbx: bash: /var/run/sipxpbx/sipxconfig.result: No such file or directory
sipXpbx: cat: /var/run/sipxpbx/sipxconfig.result: No such file or directory
sipXpbx:
sipXpbx: Check sipXvxml
sipXpbx:    bash: /var/run/sipxpbx/sipXvxml.result: No such file or directory
sipXpbx: cat: /var/run/sipxpbx/sipXvxml.result: No such file or directory
sipXpbx:
sipXpbx: Check sipxpark
sipXpbx:    bash: /var/run/sipxpbx/sipxpark.result: No such file or directory
sipXpbx: cat: /var/run/sipxpbx/sipxpark.result: No such file or directory
sipXpbx:
sipXpbx: Check sipxpresence
sipXpbx:    bash: /var/run/sipxpbx/sipxpresence.result: No such file or director
y
sipXpbx: cat: /var/run/sipxpbx/sipxpresence.result: No such file or directory
sipXpbx:
sipXpbx: Check sipstatus
sipXpbx:    bash: /var/run/sipxpbx/sipstatus.result: No such file or directory
sipXpbx: cat: /var/run/sipxpbx/sipstatus.result: No such file or directory
sipXpbx:
sipXpbx: Check sipregistrar
sipXpbx:    bash: /var/run/sipxpbx/sipregistrar.result: No such file or director
y
sipXpbx: cat: /var/run/sipxpbx/sipregistrar.result: No such file or directory
sipXpbx:
sipXpbx: Check sipauthproxy
sipXpbx:    bash: /var/run/sipxpbx/sipauthproxy.result: No such file or director
y
sipXpbx: cat: /var/run/sipxpbx/sipauthproxy.result: No such file or directory
sipXpbx:
sipXpbx: Check keepalive
sipXpbx:    bash: /var/run/sipxpbx/keepalive.result: No such file or directory
sipXpbx: cat: /var/run/sipxpbx/keepalive.result: No such file or directory
sipXpbx:
Attempting to start despite configuration problems

Starting sipXpbx:
Starting watchdog: /usr/bin/watchdog.sh: line 30: /var/run/sipxpbx/watchdog.pid:
 No such file or directory
....failure

 Waiting for keepalive to start: 20 19 18 17 16 15 14 13 12 11 10 9 8 7 6 5 4 3
2 1 failure

Starting httpd: /usr/sbin/apache2 already running.
failure

user@sipx:~$


```

---

