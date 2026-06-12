---
title: "How to make a init-script?"
date: 2009-05-23
forum: General Help
---

### Post by njb on 2009-05-23
Hello, ):P

I have a command I want to be run at every boot
#
You can run ddclient as "/usr/sbin/ddclient -daemon 300 -syslog" and put it in your startup scripts
#
this command has to be run as root who is the file owner.

:D NjB

---

### Post by taurus on 2009-05-23
You can add it to /etc/rc.local, before the exit 0.

```
gksudo gedit /etc/rc.local
```

---

