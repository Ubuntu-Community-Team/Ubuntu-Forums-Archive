---
title: "MySQL stopped working in 8.10 (Intrepid)"
date: 2010-05-21
forum: Desktop Environments
---

### Post by jakemonO on 2010-05-21
I ran an apt upgrade and now my mySQL won't start. It's a standard Intrepid install and the error I get when running mysqld --verbose is:
```
InnoDB: Error: tried to read 16384 bytes at offset 0 770048.
InnoDB: Was only able to read -1.
100521 13:59:27  InnoDB: Operating system error number 5 in a file operation.
InnoDB: Error number 5 means 'Input/output error'.
InnoDB: Some operating system error numbers are described at
InnoDB: http://dev.mysql.com/doc/refman/5.0/en/operating-system-error-codes.html
InnoDB: File operation call: 'read'.
InnoDB: Cannot continue operation.
```

I've been looking around for an answer to this problem for a day now and am admitting defeat. Can anyone assist me?

---

