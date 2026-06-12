---
title: "gtk-3 Causing Nautilus to Crash"
date: 2012-10-11
forum: Desktop Environments
---

### Post by Destructo47 on 2012-10-11
For a while now, I've been getting random Nautilus crashes. I was finally able to pull up a 'dmesg' output before the error message was pushed into the belly of the output.

The last two errors went as follows:
```
[14479.106286] pspi.exe.so[13308]: segfault at 6 ip 00000006 sp bfebe044 error 4 in pspi.exe.so[819000+1d000]
[16200.294927] nautilus[1871]: segfault at c ip 00f5cb34 sp bfa67c7c error 4 in libgtk-3.so.0.507.0[c55000+510000]

```

The first was irrelevant to the crash (and was easily remedied). The second, however, is what I'm interested in. The message tells me that there was a segfault crash. I'm not exactly an expert at interpreting these types of things, so could someone help me out here? I've seen numerous complaints on various threads, Launchpad, and other sites. It would be greatly appreciated if someone could help.

Btw, I have completely removed Unity and Compiz from my system, if that makes a difference.

---

