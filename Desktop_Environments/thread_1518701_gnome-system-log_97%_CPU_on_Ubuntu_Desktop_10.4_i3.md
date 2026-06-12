---
title: "gnome-system-log 97% CPU on Ubuntu Desktop 10.4 i386"
date: 2010-06-27
forum: Desktop Environments
---

### Post by mcook2 on 2010-06-27
On Ubuntu 10.4 Desktop i386 the gnome-system-log application, at least when monitoring my main Apache2 log (size 554 KB), drives up to 97% CPU on both processors on my AMD 3800+ X2 running [uname -a] Linux [hostname] 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux.

It will start happily, but within about two minutes I will hear the system fan crank up and if I then go run top in a terminal, I can see:

Virtual memory  79792
CPU 96% 

1 screenshot is attached.

Here is ps info I was able to capture:

```
mcook@cara:~$ sudo ps -M -Z -F -l -m -L -w -p 9360
LABEL                           F S UID        PID  PPID   LWP  C NLWP PRI  NI ADDR SZ WCHAN    RSS PSR STIME TTY          TIME CMD
unconfined                      0 - mcook     9360     1     - 97    2   -   - - 19948 -      14624   - 23:22 ?        00:19:57 gnome-system-log
unconfined                      0 S mcook        -     -  9360  0    -  80   0 -     - poll_s     -   1 23:22 -        00:00:02 -
unconfined                      1 R mcook        -     -  9365 95    -  80   0 -     - -          -   0 23:22 -        00:19:29 -
mcook@cara:~$ 
```


How should I go about reporting a bug please - at Launchpad?What extra information should I try to collect?

Thank you,

---

