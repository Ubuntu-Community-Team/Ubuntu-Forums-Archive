---
title: "Help with ddclient + OpenDNS"
date: 2009-05-29
forum: General Help
---

### Post by falconed7 on 2009-05-29
Hey all!

I'm currently haveing trouble setting up ddclient to update my IP in OpenDNS so that its services can be used after my IP address changes.

I have the following in /etc/default/ddclient:

```
# Configuration for ddclient scripts 
# generated from debconf on Fri May 29 17:48:52 EST 2009
#
# /etc/default/ddclient

# Set to "true" if ddclient should run in daemon mode
run_daemon="true"

# Set the time interval between the updates of the dynamic DNS name in seconds.
# This option only takes effect if the ddclient runs in daemon mode.
daemon_interval="300"


##
## OpenDNS.com account-configuration
##
ssl=yes
syslog=yes
use=web, web=www.whatismyip.com
server=updates.opendns.com
protocol=dyndns2
login=XXXXX
password=YYYYY
Home
```

When I restart ddclient i get the following error messages:
```
/etc/default/ddclient: 24: Home: not found
 * Restarting Dynamic DNS service update utility ddclient
WARNING:  file /etc/ddclient.conf, line 7: Invalid Value for keyword 'if' = ''
WARNING:  file /etc/ddclient.conf, line 8: Invalid Value for keyword 'server' = ''
WARNING:  file /etc/ddclient.conf, line 9: Invalid Value for keyword 'login' = ''
```

I have set my OpenDNS network name (Home) correctly whilst following the OpenDNS 'guide' for ddclient. [http://www.opendns.com/support/article/192](http://www.opendns.com/support/article/192)

Any ideas on what could be going wrong?
Thank you in advance!

---

### Post by falconed7 on 2009-05-31
Bump.

---

### Post by nucleuskore on 2009-09-16
[http://ubuntuforums.org/showthread.php?t=1264710](http://ubuntuforums.org/showthread.php?t=1264710)

---

