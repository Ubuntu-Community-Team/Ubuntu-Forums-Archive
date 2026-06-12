---
title: "BZflag 2.0.4 package problem"
date: 2006-06-28
forum: Gaming &amp; Leisure
---

### Post by NutrOn on 2006-06-28
When compiling package from source I get the following error when running sudo checkinstall.

     make[2]: Leaving directory `/home/lewis/Desktop/bzflag-2.0.4.20050930/include'make[1]: Leaving directory `/home/lewis/Desktop/bzflag-2.0.4.20050930/include'Making install in man
make[1]: Entering directory `/home/lewis/Desktop/bzflag-2.0.4.20050930/man'
make[2]: Entering directory `/home/lewis/Desktop/bzflag-2.0.4.20050930/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/man/man5" || mkdir -p -- "/usr/local/man/man5"
true_fopen == 0 for fopen64("/proc/mounts", "r")
mkdir: cannot create directory `/usr/local/man': File exists
make[2]: *** [install-man5] Error 1
make[2]: Leaving directory `/home/lewis/Desktop/bzflag-2.0.4.20050930/man'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/lewis/Desktop/bzflag-2.0.4.20050930/man'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

---------------------------------------------------------------------------------------------------------
When trying sudo dpkg -i bzflag*.deb I get:

     lewis@ubuntu:~/Desktop/bzflag-2.0.4.20050930$
lewis@ubuntu:~/Desktop/bzflag-2.0.4.20050930$ sudo dpkg -i bzflag-2.0.4.20050930.deb
dpkg: error processing bzflag-2.0.4.20050930.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bzflag-2.0.4.20050930.deb
lewis@ubuntu:~/Desktop/bzflag-2.0.4.20050930$
 
Any known fixes, work-around or problems that anyone know aboutand would help me with?
NutrOn AKA Lewis;)

---

