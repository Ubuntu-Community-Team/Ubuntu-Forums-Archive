---
title: "Memory Leak in Ubuntu 10.04 LTS version of gtkmm-2.4"
date: 2011-05-19
forum: Desktop Environments
---

### Post by BlackBuffalo on 2011-05-19
I'm doing some programming using the gtkmm and glademm libraries, and it seems that there is a memory leak somewhere--and it's not in my code, because I tried a simple application that just included the libraries, and that made the difference.  Here's my valgrind output:
==16309== HEAP SUMMARY:
==16309==     in use at exit: 120 bytes in 1 blocks
==16309==   total heap usage: 108 allocs, 107 frees, 7,233 bytes allocated
==16309== 
==16309== 120 bytes in 1 blocks are definitely lost in loss record 1 of 1
==16309==    at 0x4C274A8: malloc (vg_replace_malloc.c:236)
==16309==    by 0x9EE3148: getdelim (iogetdelim.c:68)
==16309==    by 0xC216EB2: ??? (in /lib/libselinux.so.1)
==16309==    by 0xC21F465: ??? (in /lib/libselinux.so.1)
==16309==    by 0xC20F2D2: ??? (in /lib/libselinux.so.1)
==16309== 
==16309== LEAK SUMMARY:
==16309==    definitely lost: 120 bytes in 1 blocks
==16309==    indirectly lost: 0 bytes in 0 blocks
==16309==      possibly lost: 0 bytes in 0 blocks
==16309==    still reachable: 0 bytes in 0 blocks
==16309==         suppressed: 0 bytes in 0 blocks
==16309== 
==16309== For counts of detected and suppressed errors, rerun with: -v
==16309== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 4 from 4)

I've tracked it down and basically whenever any of the following libraries are linked into the executable, the memory leak appears:
-lgtkmm-2.4 -lgdkmm-2.4 -lgiomm-2.4 -lgtk-x11-2.0 -lgdk-x11-2.0 -lgio-2.0 -lgdk_pixbuf-2.0

I'm running Ubuntu 10.04 LTS, and the gtkmm package I have installed is gtkmm-2.4-dev version 1:2.20.3-0ubuntu1

This doesn't seem to happen on a non-ubuntu machine.

Anyone else observed this?  Is there an update that resolves the memory leak?

---

