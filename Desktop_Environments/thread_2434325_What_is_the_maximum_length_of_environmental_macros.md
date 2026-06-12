---
title: "What is the maximum length of environmental macros?"
date: 2020-01-03
forum: Desktop Environments
---

### Post by jiapei100 on 2020-01-03
Normally, I predefine my environmental macros in **/etc/environment** , such as PATH and LD_LIBRARY_PATH, etc.

I happen to put **/usr/bin** etc. at the very end of **PATH**, which leads to system crash, which finally reminds me of macro **PATH** shouldn't be **TOOOOOOOOOOO** long, right?

Anyway, after trivial modification, the problem solved.

Isn't it possible to have a long enough string (say: **65536** characters) for those 2 VERY important environmental macros (**PATH** and **LD_LIBRARY_PATH**) ?


Cheers
Pei

---

### Post by TheFu on 2020-01-03
The MAX PATH and maximum pre-allocated environment space are set at compile time.  

The MAX_PATH is set for the kernel and last time I checked it was 4096.  I remember the days when it was 256 characters and we had to build our own kernels for every system inside a control center to allow longer paths.  If you follow "limits.h", I think you'll find this setting a few #includes deep.

I don't know where the max environment preallocated storage is.  Could be set in the shell.

BTW, modifying system files when only 1 userid needs the changes is a terrible plan for many reasons.  Mainly because system accounts for daemons are tested using those settings.  Changing them like it seems you'd done can easily break things.

---

