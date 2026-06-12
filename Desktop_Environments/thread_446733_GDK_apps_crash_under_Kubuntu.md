---
title: "GDK apps crash under Kubuntu"
date: 2007-05-17
forum: Desktop Environments
---

### Post by Flutterby on 2007-05-17
This has started happening to me since yesterday:

After booting into kubuntu, the first few minutes I am able to start gdk apps fine.  After a few minutes however, when I tried to start one, they all segfault.  On someone's suggestion I tried the following:

```

[45] ~% gdb `which pan`
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) r
Starting program: /usr/bin/pan
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1220614448 (LWP 5774)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1220614448 (LWP 5774)]
0xb70e3bf5 in ?? ()
(gdb) bt
#0  0xb70e3bf5 in ?? ()
#1  0xb7b4e961 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#2  0xbfa6e228 in ?? ()
#3  0x086da598 in ?? ()
#4  0x00000000 in ?? ()

```

The same #1 shows up with other apps that crash, so apparently libgdk-x11-2.0.so.0 is the problem.
However, what do I do know?  Can I fix it?
I do not have this problem when booting into "regular" ubuntu.

---

