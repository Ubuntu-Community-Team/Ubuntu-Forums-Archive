---
title: "dbus failing to start without network"
date: 2005-09-20
forum: Desktop Environments
---

### Post by nocturn on 2005-09-20
It seems that dbus on my protable fails to start when it is not connected to the network.

I traced the cause to the use of nss_ldap and the fact that the dbus UID (101) does not resolve to a user.

Is anyone else experiencing this?
Can I safely create a user with that UID to get rid of the LDAP connection errors?

Why is the service running as a non-existing user?

---

### Post by nocturn on 2005-09-21
Ok, the UID does exist (messagebus).  I do not know why it is shown numerical in the process list, but it is there.

dbus fails to start when my ldap server is not available (I'm ussing nss_ldap), I see this error in user.log:

Sep 18 17:35:21 localhost dbus-daemon-1: nss_ldap: could not connect to any LDAP server as cn=...

Any ideas how I can fix this?

---

### Post by mlomker on 2005-09-21
Forgive me for speculating here.  I assume that you are using the LDAP daemon to authenticate users to the local machine?  If that's the case then is there a setting that tells the LDAP daemon to ignore the local user accounts and require authentication by LDAP?  Perhaps there's a configuration setting that'll permit the use of LDAP and local accounts at the same time.

---

### Post by nocturn on 2005-09-21
[QUOTE=mlomker]Forgive me for speculating here.  I assume that you are using the LDAP daemon to authenticate users to the local machine?  If that's the case then is there a setting that tells the LDAP daemon to ignore the local user accounts and require authentication by LDAP?  Perhaps there's a configuration setting that'll permit the use of LDAP and local accounts at the same time.[/QUOTE]

I have an LDAP server running on another machine (my server).  My computer is a laptop with both local and LDAP users.  I would like to be able to log in with a local ID when disconnected (away from home) and use a network ID when connected.

So, Dbus actually fails when LDAP is not available, the other services seem not to care...

---

