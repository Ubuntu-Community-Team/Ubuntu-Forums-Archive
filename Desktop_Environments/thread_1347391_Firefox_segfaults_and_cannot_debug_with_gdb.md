---
title: "Firefox segfaults and cannot debug with gdb"
date: 2009-12-06
forum: Desktop Environments
---

### Post by rmjb on 2009-12-06
Hi guys,

For some reason firefox will no longer launch. Every time I run firefox it instantly returns "Segmentation fault"
I tried creating a new profile and running it in safe mode, but nothing consistently works, i.e. firefox may launch sometimes but most times the same thing will happen, only "Segmentation fault"

I tried doing firefox --debug to see if I can tell what may be causing firefox to crash instantaneously, but I only get the following output:
```
/usr/bin/gdb /usr/lib/firefox-3.5.5/firefox -x /tmp/mozargs.hLgdbQ
GNU gdb (GDB) 7.0-ubuntu
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/lib/firefox-3.5.5/firefox...(no debugging symbols found)...done.
(gdb)
``` 

Do you guys have any advice on how I can figure out what's going on with Firefox?

---

