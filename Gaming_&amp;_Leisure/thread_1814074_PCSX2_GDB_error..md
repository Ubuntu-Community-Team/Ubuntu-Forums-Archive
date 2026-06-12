---
title: "PCSX2 GDB error."
date: 2011-07-28
forum: Gaming &amp; Leisure
---

### Post by freshmeat20 on 2011-07-28
Installed PCSX2 through svn and now when I try and run through gdb i get this 

```
7fffdfb4b000-7fffdfb4e000 r-xp 00000000 08:03 5770935                    /usr/lib/libxcb-atom.so.1.0.0
7fffdfb4e000-7fffdfd4e000 ---p 00003000 08:03 5770935                    /usr/lib/libxcb-atom.so.1.0.0
Program received signal SIGABRT, Aborted.
0x00007ffff4349ba5 in raise () from /lib/libc.so.6

```

And the back trace looks like this 

```
#0  0x00007ffff4349ba5 in raise () from /lib/libc.so.6
#1  0x00007ffff434d6b0 in abort () from /lib/libc.so.6
#2  0x00007ffff438343b in ?? () from /lib/libc.so.6
#3  0x00007ffff4415537 in __fortify_fail () from /lib/libc.so.6
#4  0x00007ffff44143f0 in __chk_fail () from /lib/libc.so.6
#5  0x00007fffdeb6713c in InitADSR() () from /root/pcsx2/bin/plugins/libZeroSPU2.so.0.1.0
#6  0x00007fffdeb6a98c in SPU2init () from /root/pcsx2/bin/plugins/libZeroSPU2.so.0.1.0
#7  0x000000000044fdf3 in InitPlugins ()
#8  0x0000000000454125 in LoadPlugins ()
#9  0x000000000041b5a0 in SysInit ()
#10 0x000000000041bb85 in main ()

```

Seems like a plugin problem "libZeroSPU2.so.0.1.0". I found this link and suggests that it a problem between 64 and 32 bit unsigned longs. But I don't exactly know how to change it.  [http://code.google.com/p/pcsx2/issues/detail?id=225](http://code.google.com/p/pcsx2/issues/detail?id=225)

Any ideas? thx in advance

---

### Post by thatguruguy on 2011-07-28
Here's the official pcsx2 ppa if you're using 32-bit Ubuntu:

[https://launchpad.net/~gregory-hainaut/+archive/pcsx2.official.ppa]("https://launchpad.net/%7Egregory-hainaut/+archive/pcsx2.official.ppa")

Here's a ppa with a 64-bit build of pcsx2 (which is the one I use):

[https://launchpad.net/~micove/+archive/console]("https://launchpad.net/%7Emicove/+archive/console")

Hope that helps.

---

### Post by freshmeat20 on 2011-07-28
Thanks for the ppa!

Still wondering what that problem was though. Did it have to do with the driver I had or the way it was compiled? Was the svn install for strictly 32bit only? Idk but thanks for the tip!

---

