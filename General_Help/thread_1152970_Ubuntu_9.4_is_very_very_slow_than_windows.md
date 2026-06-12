---
title: "Ubuntu 9.4 is very very slow than windows"
date: 2009-05-08
forum: General Help
---

### Post by AlNaimi on 2009-05-08
Hi every one...
I'm new user to ubuntu, And i'm using 9.4 (64bit) With high hardward set (Core2dou 2.0 T6800) + (4 Gb ram) + (256 intel shared)....
When I was using Vista (64bit version), Nothing was going wrong, I can use Over 25 program at once with very soft movement...
Right know with ubuntu, Only one Or three operations (programs runing) and all system are died, the mouse move slowely and any moment i expect hung with system, i thought that when every body talk about lunix, the very preformance and bla bla bla was true.Nothing was correct expect virus free....
Is it something going wrong with system? Or that was ubuntu??!
plz let me know

---

### Post by slackthumbz on 2009-05-08
sounds like something wrong with your install or your configuration, I've never had a linux installation that wasn't around 2x as fast as windows.

---

### Post by AlNaimi on 2009-05-08
Thanks slackthumbz for your fast reply
However, Maybe you are right? but my situation is like i said...
I try the ubuntu system a lot of time. Opening multi programs at once, such as movie player, firefox, trasfiring huge data, webcam recording, music player...compiz full configration,,,, that never going without hunging system!!
and the mosue become slowly movement, also the video player
All the time i have to restart the system again....
Any one could let me know more how to fix that?

---

### Post by wpshooter on 2009-05-08
Probably quickest and most efficient way to fix is to re-install Ubuntu.

---

### Post by arapa on 2009-05-08
What kind of changes/modifications/installations have you made to the Ubuntu system since you first installed?

---

### Post by kay-man on 2009-05-08
can you open a terminal and run

top

and post the output? That should give some idea of processes and CPU and memory usage

---

### Post by AlNaimi on 2009-05-08
Well, some programs from add/remove applications, ubuntu tweak,wine (with no applications), Thats all....
allways updating system, clean cash and package,,,,
should i reinstall ubuntu again?!

---

### Post by AlNaimi on 2009-05-08
Top:
top - 19:35:05 up  1:29,  2 users,  load average: 0.04, 0.22, 0.99
Tasks: 146 total,   1 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  1.1%sy,  0.0%ni, 97.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3979892k total,  3958704k used,    21188k free,   169048k buffers
Swap:  2000052k total,        0k used,  2000052k free,  2973900k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5528 root      20   0  517m  89m  16m S    3  2.3   3:39.76 Xorg                                                                                            
 5865 yoyoboy   20   0  793m 283m  16m S    1  7.3   3:21.98 firefox                                                                                         
12207 yoyoboy   20   0  197m  18m  11m S    1  0.5   0:03.45 gnome-terminal                                                                                  
 2728 root      20   0 28484  800  516 S    0  0.0   0:02.27 hald-addon-stor                                                                                 
 5717 yoyoboy   20   0  233m  23m 2780 S    0  0.6   0:17.42 compiz.real                                                                                     
12230 yoyoboy   20   0 19116 1340  988 R    0  0.0   0:00.85 top                                                                                             
    1 root      20   0  4104  536  248 S    0  0.0   0:00.97 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:17.56 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:21.07 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.86 events/0                                                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.10 events/1                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0                                                                                         
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1                                                                                         
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                   
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                   
   16 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/0                                                                                       
   17 root      15  -5     0    0    0 S    0  0.0   0:00.14 kblockd/1                                                                                       
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                                                                                          
   21 root      15  -5     0    0    0 S    0  0.0   0:00.34 ata/0                                                                                           
   22 root      15  -5     0    0    0 S    0  0.0   0:00.40 ata/1                                                                                           
   23 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
   25 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
   26 root      15  -5     0    0    0 S    0  0.0   0:00.04 kseriod                                                                                         
   27 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd                                                                                           
   28 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn

---

### Post by broxigar on 2009-05-08
I think its your compiz thats creating problems, since your video card was "256 intel shared" that probaly means its onboard and thats never good for Compiz. Try disabling all the extra effects and see if it helps

---

### Post by SESF0908 on 2009-05-08
Sometimes, when i make a file operation (copy a big file, over 700MB for ex), and open firefox, the whole system slow down, i've seen this so many time, but i don't know why. If i'm not wrong, this rarely happen in v8.04.

The same happen in kubuntu v9.04 as well, but it's worse, when i open dolphin and konqueror the same time, the system crash, this does not happen frequently, but 5 times is enough for me, i use ubuntu since then.

Does anyone have a solution for this??

I used a asus F80L laptop; CPU core 2 Duo T5550; RAM 2GB; VGA Intel GMA X3100.

Sorry for my bad English.

---

### Post by astropirit on 2009-05-08
Greetings all. I am very new to ubuntu (Linux in general) I appear to be having the same problem. I am running ubuntu 9.04 32 bit. my computer seems to be running alot slower then my xp for some reason. the installation is fresh too. I am running on Intel Celeron 1.7 Ghz, 622 MB ram. and my graphics chip is an "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"

```
top - 13:03:01 up 25 min,  2 users,  load average: 0.30, 0.38, 0.48
Tasks: 111 total,   1 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.0%us,  4.7%sy,  0.0%ni, 90.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    636980k total,   504808k used,   132172k free,    32100k buffers
Swap:  1879564k total,        0k used,  1879564k free,   219484k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 3613 astropir  20   0 34556  14m 9932 S  8.0  2.4   0:09.11 gnome-terminal                                                  
 2505 root      20   0  172m  30m  14m S  0.7  5.0   2:53.41 Xorg                                                            
 3100 astropir  20   0  209m 105m  25m S  0.7 16.9   4:09.90 firefox                                                         
 3738 astropir  20   0  2448 1184  912 R  0.3  0.2   0:00.84 top                                                             
    1 root      20   0  3084 1884  564 S  0.0  0.3   0:01.76 init                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.05 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                         
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0                                                         
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                   
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0                                                       
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                          
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                    
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                          
   14 root      15  -5     0    0    0 S  0.0  0.0   0:00.44 ata/0                                                           
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                         
   16 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                   
   17 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                           
   18 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                         
   19 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                           
   20 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                       
   21 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                       
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                         
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.04 pdflush                                                         
   24 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                         
   25 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                           
   26 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea                                                 
   29 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                       
   30 root      15  -5     0    0    0 S  0.0  0.0   0:01.56 scsi_eh_1 
```

When i used to run on xp it was all fine. every thing ran fast and smooth, now minimising and maximising windows alone take forever! even if it is the only thing open. Any remedies for this?

---

### Post by pan05 on 2009-05-08
Your performance problems are relative with the intel driver that comes with jaunty.

You can read about it in the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904").

There is a couple of workarounds though. [This]("http://ubuntuforums.org/showthread.php?p=7132612") is what did the trick for me.

---

