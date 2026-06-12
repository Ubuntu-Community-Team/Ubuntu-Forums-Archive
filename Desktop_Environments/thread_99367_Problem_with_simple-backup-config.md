---
title: "Problem with simple-backup-config"
date: 2005-12-05
forum: Desktop Environments
---

### Post by henriquemaia on 2005-12-05
Hello,

When I run it, I get:

```
/home/henriquemaia/Desktop# simple-backup-config
Traceback (most recent call last):
  File "/usr/sbin/simple-backup-config", line 680, in ?
    i = SBConf()
  File "/usr/sbin/simple-backup-config", line 198, in __init__
    elif croninfo[3]=="*" and croninfo[4]=="*":
IndexError: list index out of range
```

Any ideas how to solve this?

Thanks.

---

### Post by waffen on 2005-12-06
Please, put your code.... (is python?)

---

### Post by henriquemaia on 2005-12-06
[QUOTE=waffen]Please, put your code.... (is python?)[/QUOTE]

Well, I don't know. Simple-backup-config is a program available on the repositories. 

I had it installed and used it before, but all the sudden never worked again. When I run it from the terminal, I get message posted before.

Thanks

---

### Post by waffen on 2005-12-06
uhm...the program pass a List and exceeds number of arguments...report the error to the developer :-(

---

### Post by henriquemaia on 2005-12-06
Ok. Going to do that.

Thanks, anyway.

---

