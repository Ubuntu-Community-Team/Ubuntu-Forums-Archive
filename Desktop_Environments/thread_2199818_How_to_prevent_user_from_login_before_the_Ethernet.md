---
title: "How to prevent user from login before the Ethernet is fully established?"
date: 2014-01-15
forum: Desktop Environments
---

### Post by phu004 on 2014-01-15
Hi guys,

I have a customized Ubuntu system (based on a 64bits 13.10 release) which is configured to accept users on a ldap server and mount their home drive from afs.  Everything is working except after a fresh boot, if the a user attempts to login before the wired connection icon changes to "connected", there is a good chance to crash the session for that user.   

I wonder if there is anyway to make  the login box appear after the Ethernet connection is fully established? 

Thanks in advance!

---

### Post by ian-weisser on 2014-01-16
Sure, one way is to add an Upstart condition.
The login screen is owned by lightdm.
Lightdm's start criteria is in /etc/init/lightdm.conf:
```
start on ((filesystem
           and runlevel [!06]
           and started dbus
           and plymouth-ready)
          or runlevel PREVLEVEL=S)

```

Add a stanza to the logic for network (let's assume eth0):

```
start on ((filesystem
           and runlevel [!06]
           and started dbus
           and plymouth-ready
           [COLOR=#800080]and net-device-up IFACE=eth0[/COLOR])
          or [COLOR=#800080]([/COLOR]runlevel PREVLEVEL=S
           [COLOR=#800080]and net-device-up IFACE=eth0)[/COLOR])

```



Warning: I have not tested it.

---

### Post by sisco311 on 2014-01-16
You should create a .override file instead of editing directly the .conf file. See: [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

---

### Post by ian-weisser on 2014-01-16
Excellent point! Quite right.

---

