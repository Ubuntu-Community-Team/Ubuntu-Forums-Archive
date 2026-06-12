---
title: "after installed ldap,  /etc/environment cannot be applied!"
date: 2007-08-16
forum: Desktop Environments
---

### Post by say2sky on 2007-08-16
now the file /etc/environment is

```

cat /etc/environment
LANG="en_US.UTF-8"
LANGUAGE="en_US:en:zh_CN:zh"
LC_ALL=en_US.UTF-8

```

then I ran 
```

source /etc/environment

```

to apply this file
then check the locale, i got

```

LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

```

my  /var/lib/locales/supported.d/local is

```

cat /var/lib/locales/supported.d/local
zh_CN.UTF-8 UTF-8
zh_TW.UTF-8 UTF-8
en_US.UTF-8 UTF-8

```

I also try to reboot my system, I always have same locale output as above show.

this all come after I installed openldap client on my system, I have google a lot but no answer found. Any one have met this problem and have a solution? Thank a lot for help!

---

