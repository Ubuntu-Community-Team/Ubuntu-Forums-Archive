---
title: "CD Record unsettled issues"
date: 2006-09-06
forum: Desktop Environments
---

### Post by neymac on 2006-09-06
I did the command  :~$ cdrecord -version
and got:

```
:~$ cdrecord -version
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-26-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
``` 

Does anyone know what are these unsettled issues?

---

### Post by jISh on 2006-09-06
It's just warning you that it was designed for an older kernel than the 2.6 you have now.

I wouldn't worry about it. The program works fine for you, right?

---

