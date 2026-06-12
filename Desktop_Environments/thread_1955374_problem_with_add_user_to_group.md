---
title: "problem with add user to group"
date: 2012-04-09
forum: Desktop Environments
---

### Post by forsubhi on 2012-04-09
I want to add user subhi to group realtime 
but when I execute the command the terminal tell me that the user already exists and I know that , but I want to add the user to this group 

```
[root@localhost Desktop]# adduser -g realtime subhi
adduser: user 'subhi' already exists

```

```

[root@localhost Desktop]# id subhi
uid=501(subhi) gid=503(subhi) groups=503(subhi)
```

---

### Post by forsubhi on 2012-04-09
I solved my Thread 
```

[root@localhost Desktop]# sudo usermod -a -G realtime subhi
[root@localhost Desktop]# id subhi
uid=501(subhi) gid=503(subhi) groups=503(subhi),502(realtime)
```

but I don't know why the first command didn't work . :lolflag:

---

### Post by Krytarik on 2012-04-09
> **forsubhi said:**
> but I don't know why the first command didn't work .
From the very top of its manpage:
> **NAME**[INDENT]adduser, addgroup - add a user or group to the system[/INDENT]Source: [http://manpages.ubuntu.com/manpages/oneiric/en/man8/adduser.8.html](http://manpages.ubuntu.com/manpages/oneiric/en/man8/adduser.8.html)

Regards.

---

