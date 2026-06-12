---
title: "Evolution terminates during Exchange 2007 configuration"
date: 2009-09-15
forum: Desktop Environments
---

### Post by mstjohn1974 on 2009-09-15
Hello,

I am trying on a Workstation to setup Evolution to work with Exchange 2007 via Exchange-MAPI for Evolution and it terminates during configuration. This is what the Console logs during this procedure:

evolution
** (evolution:9954): DEBUG: Loading Exchange MAPI Plugin 

** (evolution:9954): DEBUG: MAPI listener is constructed with 0 listed MAPI accounts 
** (evolution:9954): DEBUG: mailto URL command: evolution %s
** (evolution:9954): DEBUG: mailto URL program: evolution
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-ExchangeMAPI'
Create profile with myusername domainname exchangeservername
libexchangemapi-Message: exchange-mapi-connection.c:2874: exchange_mapi_create_profile: lock(connect_lock)
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Logging into the server... succeeded 
libexchangemapi-Message: exchange-mapi-connection.c:146: exchange_mapi_connection_close: lock(connect_lock)
Segmentation fault


Any Ideas about this?

---

### Post by rockfx01 on 2009-11-03
What version of Ubuntu are you running?

I just ran into this too on Ubuntu 9.04 with evolution-mapi 0.26.0.1-0ubuntu2 installed.

I ran across a [bug report]("https://bugzilla.redhat.com/show_bug.cgi?id=493661") which seems to say this issue is fixed in version 0.26.1-1 (for Fedora Core) so it may be necessary to update to a new version to resolve this, but the 9.04 repositories only have version 0.26.0.1-0.

---

### Post by i.r.id10t on 2009-11-03
Also, exchange can be set to exclude non-MS clients... here at work I can't connect via evolution using exchange info, but the mac users using entourage can, and of course the windows users using outlook.

---

### Post by mstjohn1974 on 2009-11-03
Thanks but I gave up on that for now....I just did a fresh installation on Karmic and still have the issue...I installed VirtualBox and installed a Windows XP Box with Outlook.

---

### Post by rockfx01 on 2009-11-03
> **i.r.id10t said:**
> Also, exchange can be set to exclude non-MS clients... here at work I can't connect via evolution using exchange info, but the mac users using entourage can, and of course the windows users using outlook.

It doesn't look like that is the case, given:
```
Logging into the server... succeeded 
```

Also, even if Exchange disallows the connection, Evolution shouldn't crash.

---

### Post by rchille on 2009-11-12
Noting this thread is getting old, but...

I ran across this same problem today (with 9.10). The mapi connector seems to have a bug in it that doesn't like hostnames.

I entered the IP of the my Exchange server during setup (instead of the host name) and it started working.

Well, mostly. I can't open emails without it crashing...but hopefully I can get that working.

---

### Post by tmugan on 2009-11-13
You could try the latest version of the MAPI plugin which has not been added to the Ubuntu repos yet for Karmic.

[http://www.mugan.com/2009/11/03/using-evolution-with-exchange-2007/](http://www.mugan.com/2009/11/03/using-evolution-with-exchange-2007/)

If it does not fix your problem, try logging the bug at launchpad.

---

