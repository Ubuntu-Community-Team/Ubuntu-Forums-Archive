---
title: "Maple Troubles"
date: 2011-02-11
forum: Education &amp; Science
---

### Post by tbase on 2011-02-11
I was wondering if anyone might be able to help me out with this. I'm trying to run Maple 8 in Ubuntu 10.10. Finally got it to install, now I'm getting this when I try to run it:

[INDENT]/home/tbass/maple8/bin.IBM_INTEL_LINUX/mserver: relocation error: /home/tbass/maple8/bin.IBM_INTEL_LINUX/libmaple.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

[/INDENT]I don't really know what I'm doing, I'm frankly amazed I got it to install, so I've no idea what to do here. If anyone has any ideas, I'd be very grateful.

---

### Post by Blutkoete on 2011-02-11
It appears that Maple is linked against an older version of GLIBC.

Someone using Mandriva had a similar problem ([http://mandrivausers.org/index.php?/topic/43143-maple-8-installation-problem/](http://mandrivausers.org/index.php?/topic/43143-maple-8-installation-problem/)) and obviously tried kind of compatibility mode in the end ([http://www.novell.com/coolsolutions/feature/11250.html](http://www.novell.com/coolsolutions/feature/11250.html)).

Maple 8 was also already discussed here ([http://ubuntuforums.org/showthread.php?t=38126](http://ubuntuforums.org/showthread.php?t=38126)), but that's a very old thread and I don't know if any of the solutions in one of these threads helps you or completly breaks your system.

Do you know which MATLAB version was shipped with Maple 8? A tutorial on how-to-install that MATLAB version should indirectly also be a how-to-install Maple 8 tutorial.

---

