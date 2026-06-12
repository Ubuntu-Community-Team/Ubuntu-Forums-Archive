---
title: "ERROR: glibc 2.1 or greater required"
date: 2009-01-02
forum: General Help
---

### Post by linxlvr on 2009-01-02
Hi all. 
Running 8.10 w/ restricted nvidia video drivers.
Trying to install Descent Mercenary leads me to the captioned error;

ERROR: glibc 2.1 or greater required

Locate provides following:

donius@family:/$ locate *glibc*
/etc/init.d/glibc.sh
/usr/share/aclocal/glibc2.m4
/usr/share/aclocal/glibc21.m4
donius@family:/$ 

Can anyone recommend a remedy?
Thanks 
-- 
dw

---

### Post by nemilar on 2009-01-02
Can you post the output of:

```
 /lib/libc.so.6 
```

---

### Post by linxlvr on 2009-01-03
> **nemilar said:**
> Can you post the output of:

```
 /lib/libc.so.6 
```
username:~$  /lib/libc.so.6
GNU C Library development release version 2.8.90, by Roland McGrath et al.
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 4.3.2.
Compiled on a Linux >>2.6.24-19-server<< system on 2008-09-29.
Available extensions:
	crypt add-on version 2.1 by Michael Glad and others
	GNU Libidn by Simon Josefsson
	Native POSIX Threads Library by Ulrich Drepper et al
	BIND-8.2.3-T5B
For bug reporting instructions, please see:
<http://www.gnu.org/software/libc/bugs.html>.
username:~$ 

TYIA
-- 
dw

---

