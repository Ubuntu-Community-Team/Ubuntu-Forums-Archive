---
title: "Is tcp port 4242 a trojan?"
date: 2009-04-21
forum: General Help
---

### Post by burakvarhan on 2009-04-21
Hello all,

When I type "netstat -lt" it shows that my machine is doing tcp listen on port 4242. What kind of service does Ubuntu 9.04 run on this port? Is it a trojan or some other threat?

Any comment is appreciated.
Thanks

---

### Post by jflaker on 2009-04-21
[http://www.iss.net/security_center/advice/Exploits/Ports/4242/default.htm](http://www.iss.net/security_center/advice/Exploits/Ports/4242/default.htm)

It could be.

Did you install any new software lately?

---

### Post by lovinglinux on 2009-04-21
Try this to see which program is listening.

```
sudo netstat -plntu
```

---

