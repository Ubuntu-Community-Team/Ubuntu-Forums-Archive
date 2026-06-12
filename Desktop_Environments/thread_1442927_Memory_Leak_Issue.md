---
title: "Memory Leak Issue"
date: 2010-03-30
forum: Desktop Environments
---

### Post by anspliff on 2010-03-30
Hi I'm running Ubuntu 9.10 - 64 bit on a AMD Phenom 9950 Quad core with 3.70GiB of ram also a ATI HD5780 video card.  My Issue is that after my boxs up time at about 46m 28s (thank you conky) my Memory usage is 53% 1.96GiB. Thats only with one Terminal window, and this fire fox window open. Also running is conky, awn, x-org, and a few other little apps. I didn't have this issue in 9.04 I don't think this is right!!! :) I've seen various threads about ATI drivers leaking, x-org leaking, firefox leaking, and so forth. So I ran Top and these are my top apps:
[HTML]
PID USER             PR   NI  VIRT  RES   SHR S %CPU %MEM   
 1352 root             20   0  265m 120m  32m S   14  4.4   4:47.61 Xorg               
 3229 (myname)   20   0  332m  26m  15m S    4  1.0   0:03.94 gnome-panel        
 3695 (myname)   20   0  104m 4256 2832 R    3  0.2   1:22.95 conky              
 3625 (myname)   20   0  636m 155m  28m S    2  5.6   3:29.59 firefox            
   13 root                     15  -5     0    0    0 S    2  0.0   0:05.85 ksoftirqd/3        
 3352                   20   0  240m  15m  10m S    2  0.6   0:00.51 indicator-apple    
 3228 (myname)   20   0  284m  54m 8068 S    1  2.0   0:11.54 compiz.real        
 3321 (myname)   20   0  171m  10m 8424 S    1  0.4   0:01.98 gtk-window-deco    
 3356 (myname)   20   0  205m  11m 9448 S    1  0.4   0:00.38 cpufreq-applet     
 3359 (myname)   20   0  226m  12m 9040 S    1  0.5   0:00.32 trashapplet        
 3360 (myname)   20   0  212m 9.8m 7800 S    1  0.4   0:07.37 multiload-apple    
 4165 (myname)   20   0  216m  16m  11m S    1  0.6   0:02.84 gnome-terminal     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.59 ksoftirqd/0        
   10 root      15  -5     0    0    0 S    0  0.0   0:01.30 ksoftirqd/2        
 3104 (myname)   20   0  299m 9.8m 7372 S    0  0.4   0:00.95 gnome-settings-    
 3354 (myname)   20   0  242m  15m  10m S    0  0.6   0:00.40 indicator-apple    
 3414 (myname)   20   0  223m  14m  10m S    0  0.5   0:01.76 awn-applet
[/HTML]Nothing to extreame so I decided to run Valgrind and this was my results:

[HTML]
$valgrind --tool=memcheck ls -l
==4186== Memcheck, a memory error detector
==4186== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==4186== Using Valgrind-3.5.0-Debian and LibVEX; rerun with -h for copyright info
==4186== Command: ls -l
==4186== 
total 40
drwxr-xr-x 2 (myname at my localhost) 4096 2010-03-30 01:19 Desktop
drwxr-xr-x 2 (myname at my localhost) 4096 2010-03-28 17:56 Documents
drwxr-xr-x 3 (myname at my localhost) 4096 2010-03-29 17:38 Downloads
drwxr-xr-x 2 (myname at my localhost) 4096 2010-03-28 17:56 Music
drwxr-xr-x 3 (myname at my localhost) 4096 2010-03-28 21:55 Pictures
drwxr-xr-x 2 (myname at my localhost) 4096 2010-03-28 17:56 Public
drwxr-xr-x 3 (myname at my localhost) 4096 2010-03-28 20:29 stuff
drwxr-xr-x 2 (myname at my localhost) 4096 2010-03-28 20:28 temp
drwxr-xr-x 2 (myname at my localhost) 4096 2010-03-28 17:56 Templates
drwxr-xr-x 2 (myname at my localhost) 4096 2010-03-28 17:56 Videos
==4186== 
==4186== HEAP SUMMARY:
==4186==     in use at exit: 19,566 bytes in 39 blocks
==4186==   total heap usage: 1,740 allocs, 1,701 frees, 158,103 bytes allocated
==4186== 
==4186== LEAK SUMMARY:
==4186==    definitely lost: 240 bytes in 3 blocks
==4186==    indirectly lost: 480 bytes in 20 blocks
==4186==      possibly lost: 0 bytes in 0 blocks
==4186==    still reachable: 18,846 bytes in 16 blocks
==4186==         suppressed: 0 bytes in 0 blocks
==4186== Rerun with --leak-check=full to see details of leaked memory
==4186== 
==4186== For counts of detected and suppressed errors, rerun with: -v
==4186== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 4 from 4)
[/HTML]Then I run:
[HTML]
$ valgrind --leak-check=full ls -v
==4198== Memcheck, a memory error detector
==4198== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==4198== Using Valgrind-3.5.0-Debian and LibVEX; rerun with -h for copyright info
==4198== Command: ls -v
==4198== 
Desktop    Downloads  Pictures    Templates  stuff
Documents  Music      Public    Videos       temp
==4198== 
==4198== HEAP SUMMARY:
==4198==     in use at exit: 21,078 bytes in 17 blocks
==4198==   total heap usage: 1,408 allocs, 1,391 frees, 130,550 bytes allocated
==4198== 
==4198== 120 bytes in 1 blocks are definitely lost in loss record 4 of 8
==4198==    at 0x4C25153: malloc (vg_replace_malloc.c:195)
==4198==    by 0x54BF9F8: getdelim (iogetdelim.c:68)
==4198==    by 0x503F322: ??? (in /lib/libselinux.so.1)
==4198==    by 0x50478D5: ??? (in /lib/libselinux.so.1)
==4198==    by 0x50372AA: ??? (in /lib/libselinux.so.1)
==4198==    by 0x7FF000579: ???
==4198==    by 0x7C3D4E45504F5352: ???
==4198==    by 0x69622F7273752F1F: ???
==4198==    by 0x69707373656C2F6D: ???
==4198==    by 0x444700732520656F: ???
==4198==    by 0x414F4259454B5F4C: ???
==4198==    by 0x554F59414C5F4451: ???
==4198== 
==4198== LEAK SUMMARY:
==4198==    definitely lost: 120 bytes in 1 blocks
==4198==    indirectly lost: 0 bytes in 0 blocks
==4198==      possibly lost: 0 bytes in 0 blocks
==4198==    still reachable: 20,958 bytes in 16 blocks
==4198==         suppressed: 0 bytes in 0 blocks
==4198== Reachable blocks (those to which a pointer was found) are not shown.
==4198== To see them, rerun with: --leak-check=full --show-reachable=yes
==4198== 
==4198== For counts of detected and suppressed errors, rerun with: -v
==4198== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 4 from 4)
[/HTML]Can somebody please help me translate that into what application or file is the issue. Thank you so much I look forward to your post.

---

### Post by mörgæs on 2010-03-31
Then it is probably best to carry on with 9.04 :-)

---

### Post by 3rdalbum on 2010-03-31
Top shows the top CPU users, not the top memory users - what does System Monitor say when you take a look at the "Processes" tab when sorted by memory?

---

