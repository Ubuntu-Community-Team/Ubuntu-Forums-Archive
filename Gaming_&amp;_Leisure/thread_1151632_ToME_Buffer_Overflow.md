---
title: "ToME Buffer Overflow"
date: 2009-05-07
forum: Gaming &amp; Leisure
---

### Post by NSDragon on 2009-05-07
So I've been trying to play ToME for the last few months, but I've been unable to. I get this error whenever I try to save:

```
*** buffer overflow detected ***: tome terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7fbcd57b82c7]
/lib/libc.so.6[0x7fbcd57b6170]
tome[0x51e220]
tome[0x51fad4]
tome[0x52121e]
tome[0x5213e0]
tome[0x51158b]
tome[0x49d5a9]
tome[0x49e9c7]
tome[0x49f272]
tome[0x597679]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fbcd56d75a6]
tome[0x405139]
======= Memory map: ========
00400000-00619000 r-xp 00000000 08:01 379701                             /usr/games/tome
00818000-00819000 r--p 00218000 08:01 379701                             /usr/games/tome
00819000-00829000 rw-p 00219000 08:01 379701                             /usr/games/tome
00829000-00882000 rw-p 00829000 00:00 0 
00c99000-011c0000 rw-p 00c99000 00:00 0                                  [heap]
7fbccf1d1000-7fbccf373000 rw-p 7fbccf1d1000 00:00 0 
7fbccf373000-7fbccf37f000 r-xp 00000000 08:01 801333                     /lib/libnss_files-2.9.so
7fbccf37f000-7fbccf57e000 ---p 0000c000 08:01 801333                     /lib/libnss_files-2.9.so
7fbccf57e000-7fbccf57f000 r--p 0000b000 08:01 801333                     /lib/libnss_files-2.9.so
7fbccf57f000-7fbccf580000 rw-p 0000c000 08:01 801333                     /lib/libnss_files-2.9.so
7fbccf580000-7fbccf58a000 r-xp 00000000 08:01 801343                     /lib/libnss_nis-2.9.so
7fbccf58a000-7fbccf789000 ---p 0000a000 08:01 801343                     /lib/libnss_nis-2.9.so
7fbccf789000-7fbccf78a000 r--p 00009000 08:01 801343                     /lib/libnss_nis-2.9.so
7fbccf78a000-7fbccf78b000 rw-p 0000a000 08:01 801343                     /lib/libnss_nis-2.9.so
7fbccf78b000-7fbccf7a1000 r-xp 00000000 08:01 801327                     /lib/libnsl-2.9.so
7fbccf7a1000-7fbccf9a1000 ---p 00016000 08:01 801327                     /lib/libnsl-2.9.so
7fbccf9a1000-7fbccf9a2000 r--p 00016000 08:01 801327                     /lib/libnsl-2.9.so
7fbccf9a2000-7fbccf9a3000 rw-p 00017000 08:01 801327                     /lib/libnsl-2.9.so
7fbccf9a3000-7fbccf9a5000 rw-p 7fbccf9a3000 00:00 0 
7fbccf9a5000-7fbccf9ad000 r-xp 00000000 08:01 801329                     /lib/libnss_compat-2.9.so
7fbccf9ad000-7fbccfbac000 ---p 00008000 08:01 801329                     /lib/libnss_compat-2.9.so
7fbccfbac000-7fbccfbad000 r--p 00007000 08:01 801329                     /lib/libnss_compat-2.9.so
7fbccfbad000-7fbccfbae000 rw-p 00008000 08:01 801329                     /lib/libnss_compat-2.9.so
7fbccfbae000-7fbccfbb3000 r-xp 00000000 08:01 378380                     /usr/lib/libogg.so.0.5.3
7fbccfbb3000-7fbccfdb2000 ---p 00005000 08:01 378380                     /usr/lib/libogg.so.0.5.3
7fbccfdb2000-7fbccfdb3000 r--p 00004000 08:01 378380                     /usr/lib/libogg.so.0.5.3
7fbccfdb3000-7fbccfdb4000 rw-p 00005000 08:01 378380                     /usr/lib/libogg.so.0.5.3
7fbccfdb4000-7fbccfdb8000 r-xp 00000000 08:01 801279                     /lib/libattr.so.1.1.0
7fbccfdb8000-7fbccffb7000 ---p 00004000 08:01 801279                     /lib/libattr.so.1.1.0
7fbccffb7000-7fbccffb8000 r--p 00003000 08:01 801279                     /lib/libattr.so.1.1.0
7fbccffb8000-7fbccffb9000 rw-p 00004000 08:01 801279                     /lib/libattr.so.1.1.0
7fbccffb9000-7fbccffcf000 r-xp 00000000 08:01 801309                     /lib/libgcc_s.so.1
7fbccffcf000-7fbcd01cf000 ---p 00016000 08:01 801309                     /lib/libgcc_s.so.1
7fbcd01cf000-7fbcd01d0000 r--p 00016000 08:01 801309                     /lib/libgcc_s.so.1
7fbcd01d0000-7fbcd01d1000 rw-p 00017000 08:01 801309                     /lib/libgcc_s.so.1
7fbcd01d1000-7fbcd02c2000 r-xp 00000000 08:01 378564                     /usr/lib/libstdc++.so.6.0.10
7fbcd02c2000-7fbcd04c2000 ---p 000f1000 08:01 378564                     /usr/lib/libstdc++.so.6.0.10
7fbcd04c2000-7fbcd04c9000 r--p 000f1000 08:01 378564                     /usr/lib/libstdc++.so.6.0.10
7fbcd04c9000-7fbcd04cb000 rw-p 000f8000 08:01 378564                     /usr/lib/libstdc++.so.6.0.10
7fbcd04cb000-7fbcd04de000 rw-p 7fbcd04cb000 00:00 0 
7fbcd04de000-7fbcd04fd000 r-xp 00000000 08:01 378613       Aborted
```

This has happened since 8.10, on both my old P4 2.3 GHz/1GB RAM laptop, on a newer one with a Core Duo 2.2 GHz/4GB RAM and 8.10 i686 and amd64, and 9.04 amd64.

It happened with ToME version 2.3.5 from the Ubuntu repos, and also happens with versions from 2.3.0 to 2.3.5 from the official site, compiled by me with the build tools and dev libraries from the Ubuntu repos (although they might not be the exact same errors; the one I just posted is from ubuntu 2.3.5)

So I have no idea why this happens, or how to fix it, or if I'm missing something, or even if it's happening to other people.

Help?

---

### Post by Grishka on 2009-05-07
> **NSDragon said:**
> So I've been trying to play ToME for the last few months, but I've been unable to. I get this error whenever I try to save:

```
*** buffer overflow detected ***: tome terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7fbcd57b82c7]
/lib/libc.so.6[0x7fbcd57b6170]
tome[0x51e220]
tome[0x51fad4]
tome[0x52121e]
tome[0x5213e0]
tome[0x51158b]
tome[0x49d5a9]
tome[0x49e9c7]
tome[0x49f272]
tome[0x597679]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fbcd56d75a6]
tome[0x405139]
======= Memory map: ========
00400000-00619000 r-xp 00000000 08:01 379701                             /usr/games/tome
00818000-00819000 r--p 00218000 08:01 379701                             /usr/games/tome
00819000-00829000 rw-p 00219000 08:01 379701                             /usr/games/tome
00829000-00882000 rw-p 00829000 00:00 0 
00c99000-011c0000 rw-p 00c99000 00:00 0                                  [heap]
7fbccf1d1000-7fbccf373000 rw-p 7fbccf1d1000 00:00 0 
7fbccf373000-7fbccf37f000 r-xp 00000000 08:01 801333                     /lib/libnss_files-2.9.so
7fbccf37f000-7fbccf57e000 ---p 0000c000 08:01 801333                     /lib/libnss_files-2.9.so
7fbccf57e000-7fbccf57f000 r--p 0000b000 08:01 801333                     /lib/libnss_files-2.9.so
7fbccf57f000-7fbccf580000 rw-p 0000c000 08:01 801333                     /lib/libnss_files-2.9.so
7fbccf580000-7fbccf58a000 r-xp 00000000 08:01 801343                     /lib/libnss_nis-2.9.so
7fbccf58a000-7fbccf789000 ---p 0000a000 08:01 801343                     /lib/libnss_nis-2.9.so
7fbccf789000-7fbccf78a000 r--p 00009000 08:01 801343                     /lib/libnss_nis-2.9.so
7fbccf78a000-7fbccf78b000 rw-p 0000a000 08:01 801343                     /lib/libnss_nis-2.9.so
7fbccf78b000-7fbccf7a1000 r-xp 00000000 08:01 801327                     /lib/libnsl-2.9.so
7fbccf7a1000-7fbccf9a1000 ---p 00016000 08:01 801327                     /lib/libnsl-2.9.so
7fbccf9a1000-7fbccf9a2000 r--p 00016000 08:01 801327                     /lib/libnsl-2.9.so
7fbccf9a2000-7fbccf9a3000 rw-p 00017000 08:01 801327                     /lib/libnsl-2.9.so
7fbccf9a3000-7fbccf9a5000 rw-p 7fbccf9a3000 00:00 0 
7fbccf9a5000-7fbccf9ad000 r-xp 00000000 08:01 801329                     /lib/libnss_compat-2.9.so
7fbccf9ad000-7fbccfbac000 ---p 00008000 08:01 801329                     /lib/libnss_compat-2.9.so
7fbccfbac000-7fbccfbad000 r--p 00007000 08:01 801329                     /lib/libnss_compat-2.9.so
7fbccfbad000-7fbccfbae000 rw-p 00008000 08:01 801329                     /lib/libnss_compat-2.9.so
7fbccfbae000-7fbccfbb3000 r-xp 00000000 08:01 378380                     /usr/lib/libogg.so.0.5.3
7fbccfbb3000-7fbccfdb2000 ---p 00005000 08:01 378380                     /usr/lib/libogg.so.0.5.3
7fbccfdb2000-7fbccfdb3000 r--p 00004000 08:01 378380                     /usr/lib/libogg.so.0.5.3
7fbccfdb3000-7fbccfdb4000 rw-p 00005000 08:01 378380                     /usr/lib/libogg.so.0.5.3
7fbccfdb4000-7fbccfdb8000 r-xp 00000000 08:01 801279                     /lib/libattr.so.1.1.0
7fbccfdb8000-7fbccffb7000 ---p 00004000 08:01 801279                     /lib/libattr.so.1.1.0
7fbccffb7000-7fbccffb8000 r--p 00003000 08:01 801279                     /lib/libattr.so.1.1.0
7fbccffb8000-7fbccffb9000 rw-p 00004000 08:01 801279                     /lib/libattr.so.1.1.0
7fbccffb9000-7fbccffcf000 r-xp 00000000 08:01 801309                     /lib/libgcc_s.so.1
7fbccffcf000-7fbcd01cf000 ---p 00016000 08:01 801309                     /lib/libgcc_s.so.1
7fbcd01cf000-7fbcd01d0000 r--p 00016000 08:01 801309                     /lib/libgcc_s.so.1
7fbcd01d0000-7fbcd01d1000 rw-p 00017000 08:01 801309                     /lib/libgcc_s.so.1
7fbcd01d1000-7fbcd02c2000 r-xp 00000000 08:01 378564                     /usr/lib/libstdc++.so.6.0.10
7fbcd02c2000-7fbcd04c2000 ---p 000f1000 08:01 378564                     /usr/lib/libstdc++.so.6.0.10
7fbcd04c2000-7fbcd04c9000 r--p 000f1000 08:01 378564                     /usr/lib/libstdc++.so.6.0.10
7fbcd04c9000-7fbcd04cb000 rw-p 000f8000 08:01 378564                     /usr/lib/libstdc++.so.6.0.10
7fbcd04cb000-7fbcd04de000 rw-p 7fbcd04cb000 00:00 0 
7fbcd04de000-7fbcd04fd000 r-xp 00000000 08:01 378613       Aborted
```

This has happened since 8.10, on both my old P4 2.3 GHz/1GB RAM laptop, on a newer one with a Core Duo 2.2 GHz/4GB RAM and 8.10 i686 and amd64, and 9.04 amd64.

It happened with ToME version 2.3.5 from the Ubuntu repos, and also happens with versions from 2.3.0 to 2.3.5 from the official site, compiled by me with the build tools and dev libraries from the Ubuntu repos (although they might not be the exact same errors; the one I just posted is from ubuntu 2.3.5)

So I have no idea why this happens, or how to fix it, or if I'm missing something, or even if it's happening to other people.

Help?

use the latest alpha. it's quite different, but saving works.

---

### Post by NSDragon on 2009-05-08
I'll give 3.0 a try. Just haven't considered it because, well, it's not 2.3 and I read that many things have changed in 3.0 >.>

---

