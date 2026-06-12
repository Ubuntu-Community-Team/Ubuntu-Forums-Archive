---
title: "update breaks thunderbird with segfault"
date: 2006-07-12
forum: Desktop Environments
---

### Post by geertvds on 2006-07-12
Hi,

The last updates of today (July 12) broke my mozilla thunderbird.
When I try to run it, it gives me the following segmentation fault error: 

DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131:  9149 Segmentation fault      "$prog" ${1+"$@"}

I started thunderbird in debug mode, and the following info came up in gdb:

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1219516736 (LWP 8771)]
0xb5779b8f in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
(gdb) bt
#0  0xb5779b8f in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#1  0xb575d56f in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#2  0xb5759e5a in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#3  0xb574ec3a in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#4  0xb574f77c in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#5  0xb57b53a1 in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#6  0xb573dc37 in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#7  0xb57434db in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#8  0xb57436fe in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#9  0xb59cc891 in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#10 0xb59cc930 in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#11 0xb59c8047 in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#12 0xb5740395 in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#13 0xb58a2d0e in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#14 0xb59861b4 in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#15 0xb59878f2 in NSGetModule () from /usr/lib/mozilla-thunderbird/components/libgklayout.so
#16 0xb4b53d68 in ?? () from /usr/lib/mozilla-thunderbird/components/libhtmlpars.so
#17 0x08804958 in ?? ()
#18 0x08824190 in ?? ()
#19 0xbfbca658 in ?? ()
#20 0xb4b9c454 in ?? () from /usr/lib/mozilla-thunderbird/components/libhtmlpars.so
#21 0x00000000 in ?? ()
(gdb) quit


I really need this thing to work :(

---

