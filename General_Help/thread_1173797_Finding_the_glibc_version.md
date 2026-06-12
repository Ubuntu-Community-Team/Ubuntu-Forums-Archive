---
title: "Finding the glibc version"
date: 2009-05-30
forum: General Help
---

### Post by WitchCraft on 2009-05-30
How to find out which version of glibc is running on your machine:

Go to console and type:
```

/lib/libc.so.6

```

You will get:
> 
all:~# /lib/libc.so.6
GNU C Library (EGLIBC) stable release version 2.9, by Roland McGrath et al.
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 4.3.3.
Compiled on a Linux >>2.6.26-2-amd64<< system on 2009-05-08.
Available extensions:
    crypt add-on version 2.1 by Michael Glad and others
    GNU Libidn by Simon Josefsson
    Native POSIX Threads Library by Ulrich Drepper et al
    BIND-8.2.3-T5B
For bug reporting instructions, please see:
<http://www.eglibc.org/issues/>.
all:~# 


Or you can do it via the package-managers:

On Debian:
```

sudo aptitude show libc6 

```
or
```

sudo apt-cache show libc6

```


And on RedHat/Fedora:
```

rpm -q glibc 

```

which should output something like
```

glibc-2.3.3-27.1 

```

---

### Post by ivotkl on 2012-12-10
Thank you! Now I can search how to update glibc. =P

---

