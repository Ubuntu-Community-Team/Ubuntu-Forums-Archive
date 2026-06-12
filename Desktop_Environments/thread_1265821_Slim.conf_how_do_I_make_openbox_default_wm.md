---
title: "Slim.conf how do I make openbox default wm?"
date: 2009-09-13
forum: Desktop Environments
---

### Post by gypsumwolf on 2009-09-13
Slim.conf how do I make Openbox default wm?

---

### Post by gypsumwolf on 2009-09-14
<bump>

Maybe if no one responds I will post this in a different section.

---

### Post by earthpigg on 2009-09-14
hi,

have you tried looking to slim-specific documentation, since AFAIK GDM and KDM are the only display managers that come with any official derivative of Ubuntu?

this looks like it could be promising for you: [http://slim.berlios.de/manual.php](http://slim.berlios.de/manual.php)

maybe this, also (since Ubuntu is based on debian, but debian does not have any 'default' display manager and thus knowledge is more likely to be 'display manager neutral')

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=440862](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=440862)

---

### Post by earthpigg on 2009-09-14
and o dear, dated 18 aug 2009:

[http://osdir.com/ml/debian-bugs-closed/2009-08/msg02037.html](http://osdir.com/ml/debian-bugs-closed/2009-08/msg02037.html)

---

### Post by gypsumwolf on 2009-09-14
Thanks for the info. Well maybe there is a way to make it work somehow as-is. or a work-around?

I edited the slim.conf to have open-box as the default and it works fine.

```
login_cmd           exec /usr/bin/openbox-session
```

The only problem is if I want more then one wm then I would need to figure out how to edit the login_cmd line to allow me to have open-box as the default but allow me to also switch wm's.

```
# Available sessions (first one is the default).
# The current chosen session name is replaced in the login_cmd
# above, so your login command can handle different sessions.
# see the xinitrc.sample file shipped with slim sources
sessions            default,openbox-session,(other1),(other2)
```

There is no .xinitrc in ~ in xubuntu. I created the file like some other help page stated but that did nothing.

I don't really need this but It would be nice to figure out. Maybe all I need to do is something simple like this

```
login_cmd           exec /usr/bin/openbox-session %session
```
or

```
login_cmd           exec /bin/bash -login /usr/bin/openbox-session %session
```

??

---

