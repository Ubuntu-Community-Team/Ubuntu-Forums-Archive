---
title: "Ubuntu thinks I'm Australian"
date: 2006-08-05
forum: Desktop Environments
---

### Post by Sheep Me on 2006-08-05
I've installed Ubuntu in English, but told it I had a Danish keyboard and that my time zone i that of Copenhagen. But Ubuntu thinks I'm Australian:

```


lars@lars-desktop:~$ cat /etc/apt/sources.list.backup | grep au
deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe
# deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```
```


lars@lars-desktop:~$ locale
LANG=en_AU.UTF-8
LANGUAGE=en_AU:en
LC_CTYPE="en_AU.UTF-8"
LC_NUMERIC="en_AU.UTF-8"
LC_TIME="en_AU.UTF-8"
LC_COLLATE="en_AU.UTF-8"
LC_MONETARY="en_AU.UTF-8"
LC_MESSAGES="en_AU.UTF-8"
LC_PAPER="en_AU.UTF-8"
LC_NAME="en_AU.UTF-8"
LC_ADDRESS="en_AU.UTF-8"
LC_TELEPHONE="en_AU.UTF-8"
LC_MEASUREMENT="en_AU.UTF-8"
LC_IDENTIFICATION="en_AU.UTF-8"
LC_ALL=
```

Why does it think that and how can I fix it? (I know I have to edit sources.list manually (already done).)

---

### Post by kerry_s on 2006-08-05
system> administration> language support

---

### Post by Sheep Me on 2006-08-05
Thanks. How do I set my locale to en_DK.ISO-8859-1?

---

