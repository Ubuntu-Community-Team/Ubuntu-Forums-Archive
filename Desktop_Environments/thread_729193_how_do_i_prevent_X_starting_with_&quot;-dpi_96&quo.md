---
title: "how do i prevent X starting with &quot;-dpi 96&quot;"
date: 2008-03-19
forum: Desktop Environments
---

### Post by keratos on 2008-03-19
Debian etch 4.0 , and my X is starting with a command line argument "-dpi 96" forcing a DPI that is inconsistent with my "DisplaySize x y" directive in xorg.conf

```

/usr/bin/X :0 -dpi 96 -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 TERM=linux ...

```

Quite simply,

How and where is this argument being passed.

I want X to establish DPI from the DisplaySize directive.

```

desktop:/usr/sbin# X -version

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Debian (xorg-server 2:1.3.0.0.dfsg-12)
Current Operating System: Linux desktop 2.6.18-6-amd64 #1 SMP Sun Feb 10 17:50:19 UTC 2008 x86_64
Build Date: 09 August 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present

```

thanks

---

### Post by keratos on 2008-03-19
sorry - found it in gdmsetup

duh

---

### Post by x1a4 on 2008-03-20
Hi,

You can override the -dpi option in xorg.conf by setting: 
```
Option         "DPI" "W x H"
```
in Section "Screen"

---

### Post by keratos on 2008-03-20
thanks, see above as that also worked. but thanks!

---

