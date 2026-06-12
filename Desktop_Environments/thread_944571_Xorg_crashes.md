---
title: "Xorg crashes"
date: 2008-10-11
forum: Desktop Environments
---

### Post by RRT2x7 on 2008-10-11
Hi,

I am running Dell Inspiron 1721 (AMD Turion64, 2 GB memory) with ubuntu 8.04 installed.
Mostly when I am using firefox and open sites like youtube Xorg will crash and leaves me with commandline.

Last few lines of Xorg.0.log.old are:

```
SetClientVersion: 0 9
Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().
(II) XAA: Evicting pixmaps

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6a) [0x48402a]
1: /lib/libc.so.6 [0x7f959de5c100]
2: /lib/libc.so.6(memcpy+0xd2) [0x7f959dea6dc2]
3: /usr/lib/xorg/modules//glesx.so [0x7f9598c7b7b7]
4: /usr/lib/xorg/modules//glesx.so [0x7f9598cdac4f]
5: /usr/lib/xorg/modules//glesx.so [0x7f9598cae406]
6: /usr/lib/xorg/modules//glesx.so [0x7f9598caeb34]
7: /usr/lib/xorg/modules//glesx.so [0x7f9598c2cc77]
8: /usr/lib/xorg/modules//amdxmm.so [0x7f9598a584e9]
9: /usr/bin/X [0x495d92]
10: /usr/lib/xorg/modules/extensions//libextmod.so [0x7f959d038326]
11: /usr/bin/X(Dispatch+0x2ef) [0x44eaaf]
12: /usr/bin/X(main+0x47d) [0x436b9d]
13: /lib/libc.so.6(__libc_start_main+0xf4) [0x7f959de481c4]
14: /usr/bin/X(FontFileCompleteXLFD+0x279) [0x435ed9]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch
```

I don't know how to get around this problem. Any help would be very useful.

Thanks in advance.

---

