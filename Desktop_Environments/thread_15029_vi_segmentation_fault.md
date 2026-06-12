---
title: "vi segmentation fault"
date: 2005-02-11
forum: Desktop Environments
---

### Post by totalshredder on 2005-02-11
Hey everybody!

   I have a little problem here... I've been trying to use VI(m) to edit some stuff (I want to setup dansguardian, for web filtering). Only problem is that whenever I try to run vi it simply says that I have a segmentation fault, then it quits on me. Thanks a lot guys!

Luke Demi

---

### Post by mendicant on 2005-02-11
That's pretty strange.  Try running it under gdb or strace and see where it fails.

---

### Post by totalshredder on 2005-02-11
[QUOTE=mendicant]That's pretty strange.  Try running it under gdb or strace and see where it fails.[/QUOTE]
 I'm getting:

GDB
```

GNU gdb 6.1-debian
Copyright 2004 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i386-linux"...BFD: /usr/bin/vi: invalid string offset 262144 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 327680 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 262144 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 327680 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 262144 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 262144 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 15 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 2 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 327680 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 262144 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 327680 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 262144 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 327680 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 262144 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 262144 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 15 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 2 >= 0 for section `'
BFD: /usr/bin/vi: invalid string offset 327680 >= 0 for section `'
(no debugging symbols found)...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

```

strace:
```
execve("/usr/bin/vi", ["vi", "LICENSE"], [/* 32 vars */]) = 0
uname({sys="Linux", node="ubuntu", ...}) = 0
brk(0)                                  = 0x81a5000
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
``` 

Thanks for the help. I still can't make much out of that.

---

### Post by mendicant on 2005-02-11
That sure looks like your binary is corrupt.  Can you try doing:

% sudo aptitude reinstall vim

You could also try 

% file /usr/bin/vim

just to make sure it initially seems correct.

---

### Post by totalshredder on 2005-02-11
[QUOTE=mendicant]That sure looks like your binary is corrupt.  Can you try doing:

% sudo aptitude reinstall vim

You could also try 

% file /usr/bin/vim

just to make sure it initially seems correct.[/QUOTE]
 Yes, 

 I tried them, same error.

 Is this a very common problem? Because I haven't been doing too much messing around.

---

### Post by mendicant on 2005-02-11
No, this is a pretty unusual problem.  What messing around have you done?  When you say 'same error' do you just mean it segfaults when you run 'file /usr/bin/vim'?  Does it give any output at all?

Have you noticed any other programs behaving this way?  I suppose readelf -a /usr/bin/vim fails and ldd /usr/bin/vim also screws up?  Does your filesystem need a fsck?  What platform are you running on?

---

