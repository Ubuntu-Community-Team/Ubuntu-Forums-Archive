---
title: "Kylix 3 Install Troubles"
date: 2006-08-04
forum: Desktop Environments
---

### Post by srstakey on 2006-08-04
Hi all,

I was trying to install Kylix 3 on Dapper, and I seem to have run into some problems.  The terminal gives the following 
```

[CENTER]BORLAND KYLIX 3[/CENTER]

Checking dependencies...
WARNING: could not find stdint.h
WARNING: could not locate libX11.so
Kernel version >= 2.2.0....OK
Glibc version >= 2.1.2....OK
X11 Server....OK
Libjpeg version >= 6.2.0....OK
Libgtk version >= 1.2.0....OK

```

Is there any way to get this installed?  I am a beginning programer (one of my teachers is really advanced in Delphi) and I would like to get this working over on Linux.  Thanks in advance!

---

### Post by maniacmusician on 2006-08-05
Well it just looks like unresolved dependencies.

I looked up Kylix and it doesn't look like something that would be available through synaptic as it is commercial. stdint.h seems to be a header file that should be part of a compiler and libX11 logically seems to be an X11 library...I would recommend contacting borland and asking them for those files or packages that can resolve your dependencies. Those should have been included with the program, or at least you should have been told about any dependencies that you needed to meet.

---

