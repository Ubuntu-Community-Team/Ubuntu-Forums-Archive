---
title: "Amarok is Crashing, alot"
date: 2006-02-05
forum: Desktop Environments
---

### Post by Connollyir on 2006-02-05
This seems to be a recurring issue with me.... every time I get it working and stable, I upgrade teh system or something and Amarok starts crashing again. This time, I upgraded Ubuntu and it broke Amarok. My first instincts told me that since I recently updated, something might not agree with the 1.3.7 version of Amarok I was running - so I upgraded to 1.3.8. Still no good. I completely removed Amarok and its dependancies then reinstalled everything with only the Arts engine to help avoid any conflicts. 

It still crashes, but not unless I change songs a lot. When I do some skipping ahead it will crash once every 10-20 songs. I get these debugging messages:

======== DEBUG INFORMATION  =======
Engine:     arts-engine
Build date: Jan 19 2006
CC version: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
KDElibs:    3.4.3
TagLib:     1.3.1
NDEBUG:     true
==== file /usr/lib/amarok/amarokapp =======
/usr/lib/amarok/amarokapp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), stripped


==== (gdb) bt =====================
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
[Thread debugging using libthread_db enabled]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()


==== kdBacktrace() ================



======== DEBUG INFORMATION  =======
Engine:     arts-engine
Build date: Jan 19 2006
CC version: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
KDElibs:    3.4.3
TagLib:     1.3.1
NDEBUG:     true
==== file /usr/lib/amarok/amarokapp =======
/usr/lib/amarok/amarokapp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), stripped


==== (gdb) bt =====================
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".


==== kdBacktrace() ================

Any help??

-Ian

---

### Post by debernardis on 2006-02-05
I resolved my problems with Amarok by compiling the SVN version as described here: [http://www.ubuntuforums.org/showthread.php?t=80492&highlight=amarok+engine](http://www.ubuntuforums.org/showthread.php?t=80492&highlight=amarok+engine)

When I tried that, for a few times it didn't complete compiling, complaining for some dependencies. It was enough to apt-get install them, though.

---

### Post by stangbang on 2006-02-06
The reason it is crashing is because the libtag file is version 1.3 and not version 1.4
What I did to fix this was download the 1.4 version of the libtag file from [http://www.czessi.net](http://www.czessi.net) and install it with dpkg

Check this post for more info [http://www.ubuntuforums.org/showthread.php?t=124698](http://www.ubuntuforums.org/showthread.php?t=124698)

There is also a 1.3.8 version available, although the same problem with the libtag version is there to.

---

### Post by Connollyir on 2006-02-06
Ok I updated my sources with the ones from czessi,net and updated/upgraded the system - we will see if it works. I read your post and it seems that we had the same problem, I wonder why Amarok didn't update the libtag dependancy to 1.4 with the new version? It seems to be working well though, I will be sure to bookmark that site as well.

-Thanks

-Ian

---

