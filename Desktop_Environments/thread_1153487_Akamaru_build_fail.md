---
title: "Akamaru build fail"
date: 2009-05-08
forum: Desktop Environments
---

### Post by giannoug on 2009-05-08
Akamaru doesn't feel like compiling on my EEE.. don't know why. Google doesn't help, only 3 or 4 results without a proper solution come up when searching for the error(s).
```

giannoug@EEEbuntu:~/dev/kiba/akamaru$ ./autogen.sh --prefix="/usr"
checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
configure.in:51: error: AC_SUBST: `"$AKAMARU_REQUIRES"' is not a valid shell variable name
configure.in:51: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1
giannoug@EEEbuntu:~/dev/kiba/akamaru$ 

```
Am I missing a dependency or what?

---

### Post by giannoug on 2009-05-09
Sorry for bumping this.. it only got 20 views. There must be a solution, or I am missing sth..
Help desperately needed :(

---

### Post by quentindemetz on 2009-05-09
I've got exactly the same problem here, and I haven't found any solution. Running Jaunty w/ KDE. Help needed.:(

---

### Post by alinef on 2009-05-16
> **giannoug said:**
> Akamaru doesn't feel like compiling on my EEE.. don't know why. Google doesn't help, only 3 or 4 results without a proper solution come up when searching for the error(s).
```

giannoug@EEEbuntu:~/dev/kiba/akamaru$ ./autogen.sh --prefix="/usr"
checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
configure.in:51: error: AC_SUBST: `"$AKAMARU_REQUIRES"' is not a valid shell variable name
configure.in:51: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1
giannoug@EEEbuntu:~/dev/kiba/akamaru$ 

```Am I missing a dependency or what?

This autoconf version handle variables differently. All you have to do is to change configure.in (line 51)

```

AC_SUBST("$AKAMARU_REQUIRES")

```to
```

AC_SUBST(AKAMARU_REQUIRES)

```

---

### Post by giannoug on 2009-05-16
> **alinef said:**
> This autoconf version handle variables differently. All you have to do is to change configure.in (line 51)

```

AC_SUBST("$AKAMARU_REQUIRES")

```to
```

AC_SUBST(AKAMARU_REQUIRES)

```

Thank you! It worked!

---

