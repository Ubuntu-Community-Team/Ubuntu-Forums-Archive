---
title: "Help with /usr/include files - they all get input/output errors"
date: 2009-02-08
forum: General Help
---

### Post by TyrantWave on 2009-02-08
I've recently had to format my HD, so I've done a complete reinstall.

I've now got a problem that whenever I try to compile a program (Using g++) that has #includ <iostream> or #include "iostream", I get the following errors:

```
In file included from /usr/include/c++/4.3/i486-linux-gnu/bits/gthr-default.h:44,
                 from /usr/include/c++/4.3/i486-linux-gnu/bits/gthr.h:132,
                 from /usr/include/c++/4.3/ext/atomicity.h:39,
                 from /usr/include/c++/4.3/bits/ios_base.h:46,
                 from /usr/include/c++/4.3/ios:48,
                 from /usr/include/c++/4.3/ostream:45,
                 from /usr/include/c++/4.3/iostream:45,
                 from primecheck.cpp:4:
/usr/include/unistd.h:554:27: error: /usr/include/bits/confname.h: Input/output error

```

It looks like the files are corrupt (Trying to open confname.h just gets errors).

Is there anything I can do to fix this?

---

### Post by geirha on 2009-02-08
Sounds like you should force a filesystem check. To do that, boot the ubuntu cd, and in the live session, run gparted (System -> Administration -> Partition editor), mark at least the linux partition where /usr/include is located, right-click and select check.

Then hit the apply button at the top.

---

### Post by TyrantWave on 2009-02-08
I just tried that, still didn't work :(

The check didn't report any errors either.

---

### Post by geirha on 2009-02-08
An Input/Output error like that sounds to me like it has problems reading the file, either because of a filesystem error or because it has problems reading from the hard drive. I might be wrong though.

Try reinstalling the package that installs those header files.
```
sudo aptitude reinstall libc6-dev
```

Also, check dmesg. See if there are any error messages relating to the hard drive.
```
dmesg
```

---

### Post by TyrantWave on 2009-02-08
Thanks!
Reinstalling the packages worked perfectly, I can compile and run now :D
*dances a happy dance*

---

