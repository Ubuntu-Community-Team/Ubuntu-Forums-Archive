---
title: "After I upgraded Pidgin, Now I get this error...(Code posted)"
date: 2009-06-10
forum: General Help
---

### Post by otz070 on 2009-06-10
```
dpkg: parse error, in file `/var/lib/dpkg/available' near line 31930 package `pidgin':
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Please help me fix this...I can't do anything until I get this fixed, and I have alot to do...

Thanks

---

### Post by Soul-Sing on 2009-06-10
Try with a ```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by otz070 on 2009-06-11
umm it's still not fixed, I tried the earlier suggestion, it unfortunatly didn't work...I removed pidgin using the recovery mode...

So now I end up digging deeper and deeper into this, nipping at it little by little, anyway, I got some things to work, but now some is worse and some is better, it freezes randomly, programs don't want to run, (sometimes it seems like I have to make sure the last one is closed before I run another one...)

anyway, I ran lshw just for the heck of it... to see if it might give me any warning about my hardware or something, anyway here is what came up at the end:
```
*** glibc detected *** lshw: corrupted double-linked list: 0x0000000001a67b30 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f84992e928c]
/lib/libc.so.6(cfree+0x8c)[0x7f84992ecc1c]
/usr/lib/libstdc++.so.6(_ZNSsD1Ev+0x3e)[0x7f8499887bae]
lshw[0x43e219]
/lib/libc.so.6(exit+0xe0)[0x7f84992aa110]
/lib/libc.so.6(__libc_start_main+0xfb)[0x7f84992931cb]
lshw(__gxx_personality_v0+0xf1)[0x403859]
======= Memory map: ========
00400000-004be000 r-xp 00000000 08:03 389222                             /usr/bin/lshw
006bd000-006bf000 rw-p 000bd000 08:03 389222                             /usr/bin/lshw
006bf000-02a11000 rw-p 006bf000 00:00 0                                  [heap]
7f8490000000-7f8490021000 rw-p 7f8490000000 00:00 0 
7f8490021000-7f8494000000 ---p 7f8490021000 00:00 0 
7f8496a70000-7f8497e71000 rw-p 7f8496a70000 00:00 0 
7f8498ff4000-7f8499074000 r-xp 00000000 08:03 203046                     /lib/libm-2.7.so
7f8499074000-7f8499273000 ---p 00080000 08:03 203046                     /lib/libm-2.7.so
7f8499273000-7f8499275000 rw-p 0007f000 08:03 203046                     /lib/libm-2.7.so
7f8499275000-7f84993cd000 r-xp 00000000 08:03 203042                     /lib/libc-2.7.so
7f84993cd000-7f84995cd000 ---p 00158000 08:03 203042                     /lib/libc-2.7.so
7f84995cd000-7f84995d0000 r--p 00158000 08:03 203042                     /lib/libc-2.7.so
7f84995d0000-7f84995d2000 rw-p 0015b000 08:03 203042                     /lib/libc-2.7.so
7f84995d2000-7f84995d7000 rw-p 7f84995d2000 00:00 0 
7f84995d7000-7f84995e4000 r-xp 00000000 08:03 202992                     /lib/libgcc_s.so.1
7f84995e4000-7f84997e4000 ---p 0000d000 08:03 202992                     /lib/libgcc_s.so.1
7f84997e4000-7f84997e5000 rw-p 0000d000 08:03 202992                     /lib/libgcc_s.so.1
7f84997e5000-7f84998d4000 r-xp 00000000 08:03 388938                     /usr/lib/libstdc++.so.6.0.9
7f84998d4000-7f8499ad4000 ---p 000ef000 08:03 388938                     /usr/lib/libstdc++.so.6.0.9
7f8499ad4000-7f8499ada000 r--p 000ef000 08:03 388938                     /usr/lib/libstdc++.so.6.0.9
7f8499ada000-7f8499add000 rw-p 000f5000 08:03 388938                     /usr/lib/libstdc++.so.6.0.9
7f8499add000-7f8499af0000 rw-p 7f8499add000 00:00 0 
7f8499af0000-7f8499b0d000 r-xp 00000000 08:03 203039                     /lib/ld-2.7.so
7f8499ced000-7f8499cf0000 rw-p 7f8499ced000 00:00 0 
7f8499d09000-7f8499d0d000 rw-p 7f8499d09000 00:00 0 
7f8499d0d000-7f8499d0f000 rw-p 0001d000 08:03 203039                     /lib/ld-2.7.so
7fffa1ccd000-7fffa1d0f000 rw-p 7ffffffbd000 00:00 0                      [stack]
7fffa1dfe000-7fffa1e00000 r-xp 7fffa1dfe000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted

```
I've never had that come up before... so what exactly does that mean??

Thanks:)

---

