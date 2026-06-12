---
title: "configuring apache to listen to ports accesible by network"
date: 2009-01-11
forum: General Help
---

### Post by Ozeuss on 2009-01-11
Currently, the directive in ports.conf is 
Listen 127.0.0.1:80

I want to be able to access my server from other computers in my home network, but not from outside of it.
Would adding a directive like "Listen 192.168.1.4:80" Do?

---

### Post by bluefrog on 2009-01-11
apache server is 192.168.1.4

just access [http://192.168.1.4](http://192.168.1.4) from your other computers.

---

### Post by Ozeuss on 2009-01-11
I can't access 192.168.1.4 with a listen 127.0.01:80 directive. because it accepts only request from the localhost.
That's why i asked if about "listen 192.168.1.4:80". This works, i was wondering whether it the best approach, also security wise.
Thanks.

---

### Post by cariboo on 2009-01-11
Just change:

> 127.0.01:80 

to

```
*:80
```

Jim

---

### Post by Dr Small on 2009-01-11
Tell Apache to listen on all interfaces, is quite simple:
```
*:80
```

Instead of just localhost.

---

