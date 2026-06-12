---
title: "Problem getting apcupsd slave  running"
date: 2006-08-23
forum: Desktop Environments
---

### Post by BrianK on 2006-08-23
I've got an APC UPS.  it's powering two of my servers, but is only connected to one of them via usb cable.  On the one server that it's connected to, I have apcupsd configured & running & get good data when I do "apcaccess status".  

My problem is this - I can't get server #2 (ares) to see server #1 (uranium) as far as apcupsd goes.  I've tried numerous configs based on suggestions from [http://www.apcupsd.com/manual/Master_Slave_Configurations.html](http://www.apcupsd.com/manual/Master_Slave_Configurations.html) (that and other pages on the same site), but always get the same message:

```

 # /etc/init.d/apcupsd restart
Restarting APC UPS power management: Stopping APC UPS power management: apcupsd.
Starting APC UPS power management: apcupsd.

Broadcast Message from root@ares.hero.com
        (somewhere) at 19:30 ...

Warning communications lost with UPS ares.hero.com

```
-or-
```
# apcaccess status
FATAL ERROR in apcaccess.c at line 252
tcp_open: cannot connect to server localhost on port 3551.
ERR=Connection refused

```
 where "ares.hero.com" is the local machine - not the one with the UPS connected via usb.  Neither "ares.hero.com nor localhost or the ips associated with either are in the apcupsd.conf file anywhere.

Has anyone gotten this to work?

---

