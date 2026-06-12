---
title: "Java memory leaks"
date: 2008-12-05
forum: Desktop Environments
---

### Post by Chris on 2008-12-05
Something weird is going on with Java.  This has been a problem since at least 8.04 and still appears in 8.10.  Both 32-bit and 64-bit versions appear to have the same problem.

If I do I full desktop install of Ubuntu (eg. ubuntu-8.10-alternate-i386.iso) then Java applications work fine.

However, if I do a server or minimal install (mini.iso net install, etc) then Java applications leak memory like crazy until eventually the kernel kills the process.  It appears to have nothing to do with Java itself because it affects the sun-java6-jre install, OpenJDK install, and I tried an install of the latest JRE from Sun.  They all have the same behavior.  Both console-only (server) and GUI applications leak.

Anyone know what could possibly be going on here?  Obviously the full desktop install is doing something different (installing something extra, different config, or something).  It appears to affect all Java applications.

---

### Post by dumbfounder on 2009-06-23
I am seeing the same problem with 9.04. It made my life a living hell the past 3 days and eventually I had to run 2 applications and then a script to cycle between them and balance to make sure that they were always up (takes >5 minutes to restart them). I was pulling my hair out trying to figure out why my app was leaking, but then I just tried running it on an older machine running Fedora Core 4 and there is no memory leak at all.

I am curious, is this a linux kernel problem, or something related just to Ubuntu? I hope it isn't a kernel problem, installing FC4 on a new machine will make me quite sad.

---

