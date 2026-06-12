---
title: "Locale"
date: 2006-06-27
forum: Desktop Environments
---

### Post by Jan Jansen on 2006-06-27
I want my locale to be Norwegian, but I want my programmes to be in English.

That is: I want collation, date/time format and such to be Norwegian, but I don't want to use the Norwegian translations of apps. Is there an easy way to accomplish this?

---

### Post by bjourne on 2006-06-27
Add this to the end of your .bashrc:

[PHP]
unset LANG
LC_CTYPE="no_NO.UTF-8"
LC_TIME="no_NO.UTF-8"
LC_COLLATE="no_NO.UTF-8"
LC_MONETARY="no_NO.UTF-8"
LC_PAPER=no_NO
LC_ADDRESS="no_NO.UTF-8"
LC_TELEPHONE="no_NO.UTF-8"
LC_MEASUREMENT="no_NO.UTF-8"
[/PHP]

EACH LC_* variable controls one aspect of your locale. So you set them to your locale ("no_NO.UTF-8") and leave the rest with the default value ("POSIX").

---

### Post by Jan Jansen on 2006-06-27
I tried your suggestion, then this: 
```

unset LANG
LC_CTYPE="nb_NO.utf8"
LC_TIME="nb_NO.utf8"
LC_COLLATE="nb_NO.utf8"
LC_MONETARY="nb_NO.utf8"
LC_PAPER="nb_NO.utf8"
LC_ADDRESS="nb_NO.utf8"
LC_TELEPHONE="nb_NO.utf8"
LC_MEASUREMENT="nb_NO.utf8"

``` 

but

```

$ locale
LANG=
LANGUAGE=en_GB:en
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
$ locale -a
C
POSIX
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
nb_NO.utf8

```

---

