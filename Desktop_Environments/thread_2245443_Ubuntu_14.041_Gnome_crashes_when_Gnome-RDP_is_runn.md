---
title: "Ubuntu 14.041 Gnome crashes when Gnome-RDP is running"
date: 2014-09-23
forum: Desktop Environments
---

### Post by hockeybum27 on 2014-09-23
Ubuntu 14.041 x64 (upgraded from 12.04) on DellLatitude E650 series

Ever since upgrading from 12.04 to 14.041, the Gnome desktop periodically crashes when I'm running Gnome RDP.  It doesn't happen every session, and it doesn't always happen when the RDP session is the active window.

When the crash occurs, I get a black screen with a cursor blinking in the upper-left corner.  I can switch to other terminal sessions (i.e., ctr+alt+ f2 to get to terminal 2).  I can log in and do other things, like check log files or reboot.

I checked several of the logs in /var/log; the one that jumps out at me is the Xorg.0.log file.  Below is an excerpt from when it crashed:

```
[ 20337.195] (EE) intel(0): Failed to submit rendering commands, disabling acceleration. 
[ 20337.196] (EE)  
[ 20337.196] (EE) Backtrace: 
[ 20337.197] (EE) 0: /usr/bin/X (xorg_backtrace+0x48) [0x7f78fa781d28] 
[ 20337.197] (EE) 1: /usr/bin/X (0x7f78fa5d9000+0x1aca19) [0x7f78fa785a19] 
[ 20337.197] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f78f96d6000+0x10340) [0x7f78f96e6340] 
[ 20337.197] (EE) 3: /lib/x86_64-linux-gnu/libc.so.6 (0x7f78f80f4000+0x809b1) [0x7f78f81749b1] 
[ 20337.197] (EE) 4: /lib/x86_64-linux-gnu/libc.so.6 (__libc_malloc+0x60) [0x7f78f8177230] 
[ 20337.197] (EE) 5: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x7f78f9221000+0x5b75b) [0x7f78f927c75b] 
[ 20337.197] (EE) 6: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x7f78f9221000+0x5ce3c) [0x7f78f927de3c] 
[ 20337.197] (EE) 7: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (pixman_region_union+0xbb) [0x7f78f927f45b] 
[ 20337.197] (EE) 8: /usr/bin/X (DamageReportDamage+0x172) [0x7f78fa70b602] 
[ 20337.197] (EE) 9: /usr/bin/X (0x7f78fa5d9000+0x132d0a) [0x7f78fa70bd0a] 
[ 20337.198] (EE) 10: /usr/bin/X (0x7f78fa5d9000+0x136023) [0x7f78fa70f023] 
[ 20337.198] (EE) 11: /usr/bin/X (0x7f78fa5d9000+0x51f71) [0x7f78fa62af71] 
[ 20337.198] (EE) 12: /usr/bin/X (0x7f78fa5d9000+0x55a1e) [0x7f78fa62ea1e] 
[ 20337.198] (EE) 13: /usr/bin/X (0x7f78fa5d9000+0x598aa) [0x7f78fa6328aa] 
[ 20337.198] (EE) 14: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f78f8115ec5] 
[ 20337.198] (EE) 15: /usr/bin/X (0x7f78fa5d9000+0x44dde) [0x7f78fa61ddde] 
[ 20337.198] (EE)  
[ 20337.198] (EE) Segmentation fault at address 0x10 
[ 20337.198] (EE)  
Fatal server error: 
[ 20337.199] (EE) Caught signal 11 (Segmentation fault). Server aborting 
[ 20337.199] (EE)  
[ 20337.199] (EE)  
Please consult the The X.Org Foundation support  
         at http://wiki.x.org 
 for help.  
[ 20337.199] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information. 
[ 20337.199] (EE)  
[ 20337.199] (II) AIGLX: Suspending AIGLX clients for VT switch 
[ 20337.242] (EE) Server terminated with error (1). Closing log file. 

```

Any ideas on what to check/do next?  Any help as always is greatly appreciated!

Thanks in advance!

---

