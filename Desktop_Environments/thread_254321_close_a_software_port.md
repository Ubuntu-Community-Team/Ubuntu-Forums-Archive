---
title: "close a software port?"
date: 2006-09-09
forum: Desktop Environments
---

### Post by enopepsoo on 2006-09-09
Hello,

I just ran this command:
[HTML]nc -v -z 127.0.0.1 1-1024[/HTML]
and I received this output:
```
localhost.localdomain [127.0.0.1] 445 (microsoft-ds) open
localhost.localdomain [127.0.0.1] 139 (netbios-ssn) open
localhost.localdomain [127.0.0.1] 22 (ssh) open

```
I don't use active directory or samba on my network.  This port is blocked at my router, but I was wondering, how would I close it in Ubuntu?

Thanks!

:-\"

---

### Post by lamego on 2006-09-09
You must have samba running and sshd, thats why they are open:
Check for listening programs with:
```
netstat -tl
```

---

