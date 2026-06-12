---
title: "dapper: /dev/mem and /dev/kmem not readable"
date: 2006-09-04
forum: Desktop Environments
---

### Post by mael on 2006-09-04
hi
i'd like to dump /dev/mem or /dev/kmem with dd in case an app crashed to recover filled in text eg firefox and online formulars

with hoary this worked fine (as root of course):
```
dd if=/dev/mem of=/tmp/mem.dd
```

but with dapper i get this:
```
dd: reading `/dev/mem': Operation not permitted
2056+0 records in
2056+0 records out
1052672 bytes (1.1 MB) copied, 0.149356 seconds, 7.0 MB/s
```

the permissions seemed to be correct:
```
ls -la /dev/*mem
crw-r----- 1 root kmem 1, 2 2006-05-22 16:25 /dev/kmem
crw-r----- 1 root kmem 1, 1 2006-09-04 10:00 /dev/mem
```

i googled but didn't find anything. i know it's a security protection but i don't care about that ;)

any ideas how to get access?
thanks!

---

### Post by mael on 2006-09-04
i did some more digging after i saw that msg in dmesg:
```
Program dd tried to read /dev/mem between 101000->101200.
```

has it sth to do with sysctl settings like 
```
kernel.cap-bound = -257
```
?

see also [http://lwn.net/Articles/144843/](http://lwn.net/Articles/144843/) and [http://lwn.net/1999/1202/kernel.php3](http://lwn.net/1999/1202/kernel.php3) and [http://lwn.net/1999/1202/capabilities.php3:](http://lwn.net/1999/1202/capabilities.php3:)
CAP_SYS_RAWIO Allow access to ioperm and iopl #

*?*

---

### Post by Endolith on 2008-05-23
I would like to know how to do this, too.  I've done it before when programs crashed, but I get the "Operation not permitted" error.

[http://www.hackszine.com/blog/archive/2008/03/recover_data_from_ram_after_a.html](http://www.hackszine.com/blog/archive/2008/03/recover_data_from_ram_after_a.html)

*Sigh*  I guess I have to retype it all.  There should be a program that does this automatically.

---

