---
title: "beryl problems"
date: 2007-01-23
forum: Desktop Environments
---

### Post by nishoba on 2007-01-23
my ubuntu is up-todate
i have installed xgl and beryl under ubuntu 6.10, i have ati fglrx drivers
and they are working
i have made a separate session to load xgl with beryl
i start the session and start beryl with:

when i start it i get this:
```
tihomir@LinUX:~$ sudo beryl-manager 
Password:
tihomir@LinUX:~$ XGL Present
Reloading options
beryl-xgl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl-xgl: Plugin 'dbus':initDisplay failed
beryl-xgl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen!

(emerald-theme-manager:4965): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work. 

```

what does this mean?
under emerald theme manager i cant change themes, i click on one but the theme stays the same until the next start of beryl-manager

hlp

---

### Post by cinnix on 2007-01-26
highlight the theme, right click on beryl manager, then "Reload Window Decorator", semi-instant themage.

---

