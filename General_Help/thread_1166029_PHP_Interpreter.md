---
title: "PHP Interpreter"
date: 2009-05-21
forum: General Help
---

### Post by waffen on 2009-05-21
Hello,

I try to setup in Eclipse IDE the Xdebug, but I dont know whats the path to the php5 interpreter?

I use Jaunty 64bits and I has installed LAMP from synaptic.

Thanks!

Mario

---

### Post by apjone on 2009-05-21
using whereis from a terminal I get. Yours may be different. /usr/bin/** is normally where the actuial binary sits so that the best chance.

```

:~$ whereis php5
php5: /usr/bin/php5 /etc/php5 /usr/lib/php5 /usr/include/php5 /usr/share/php5 /usr/share/man/man1/php5.1.gz

```

---

### Post by waffen on 2009-05-21
This is my terminal result:

```

mario@mario-laptop:~$ whereis php5
php5: /etc/php5 /usr/lib/php5 /usr/lib64/php5 /usr/share/php5

```

I dont see the /usr/bin/php5 I use jaunty amd64 its different here or my php installation are bad?

Thanks!

---

### Post by apjone on 2009-05-21
Could try without the 5
```
whereis php
```

---

### Post by waffen on 2009-05-21
```

mario@mario-laptop:~$ whereis php
php:

```

Any idea? I use it in my laptop for development, so if I need to reinstall it I think there is no problem for me. If this is the best way to fix this, how reinstall php?

I install LAMP from synaptic using the packages for task listing..

Thanks!

---

### Post by waffen on 2009-05-21
OK I just found the error: the default Ubuntu LAMP installation not install php5.cli.... installing that all work!

Thanks!

---

### Post by apjone on 2009-05-22
Good spot ;)

---

