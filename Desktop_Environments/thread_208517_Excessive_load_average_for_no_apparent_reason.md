---
title: "Excessive load average for no apparent reason"
date: 2006-07-03
forum: Desktop Environments
---

### Post by HippoMan on 2006-07-03
I'm running kubuntu under Dapper on two separate machines, and in both cases, I'm noticing an excessive load average for no apparent reason.  In the** top** output enclosed below, notice that each cpu is almost completely idle, and that there is hardly any memory or cpu time allocated to the processes, Nonetheless, the load average is still over 2.00.

By the way, the **top** output is sorted by cpu time, and the memory and cpu utilization do not change appreciably from the values shown below ... nor does the load average drop below 2.00 for any significant amount of time.

Can anyone explain why I have such a high load average for no clearly apparent reason?

Thanks in advance.

Here's the **top** output from one of the machines.  The other system shows similar results:

```
top - 17:50:14 up 16:57,  2 users,  load average: 2.10, 2.26, 2.23
Tasks:  94 total,   1 running,  93 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.7% us,  1.3% sy,  0.0% ni, 97.7% id,  0.3% wa,  0.0% hi,  0.0% si
Cpu1  :  0.0% us,  0.7% sy,  0.0% ni, 99.3% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1034184k total,   663276k used,   370908k free,   126556k buffers
Swap:   755012k total,        0k used,   755012k free,   358284k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                               
 6526 root      15   0 96788  11m 3608 S    1  1.2 107:18.05 Xorg                                   
 6688 hippo     15   0 26844  12m 9.9m S    0  1.2   0:03.77 kwin                                   
 6707 hippo     16   0 25036  10m 8808 S    0  1.0   0:00.32 klipper                                
 6875 root      20   5  5228 2192 1620 S    0  0.2   0:07.55 urxvt                                  
11444 root      21   5  2200 1116  856 R    0  0.1   0:00.95 top                                    
    1 root      16   0  1564  524  460 S    0  0.1   0:01.61 init                                   
    2 root      RT   0     0    0    0 S    0  0.0   0:00.10 migration/0                            
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                            
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                             
    5 root      RT   0     0    0    0 S    0  0.0   0:00.08 migration/1                            
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                            
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                             
    8 root      10  -5     0    0    0 S    0  0.0   0:00.24 events/0                               
    9 root      10  -5     0    0    0 S    0  0.0   0:00.01 events/1                               
   10 root      10  -5     0    0    0 S    0  0.0   0:00.02 khelper                                
   11 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthread                                
   14 root      10  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0                              
   15 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                              
   16 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                 
  116 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                
  117 root      15   0     0    0    0 S    0  0.0   0:01.00 pdflush                                
  119 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                  
  120 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                  
  118 root      25   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                
  708 root      10  -5     0    0    0 S    0  0.0   0:00.02 kseriod                                
  794 root      15   0     0    0    0 S    0  0.0   0:00.00 kirqd                                  
 1758 root      11  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                              
 1963 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                  
 1974 root      20   0     0    0    0 S    0  0.0   0:00.00 khpsbpkt                               
 1991 root      15   0     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                            
 2087 root      10  -5     0    0    0 S    0  0.0   0:00.03 reiserfs/0                             
 2088 root      10  -5     0    0    0 S    0  0.0   0:00.04 reiserfs/1                             
 2311 root      17  -4  2544 1028  368 S    0  0.1   0:00.48 udevd                                  
 3126 root      20   0     0    0    0 S    0  0.0   0:00.00 shpchpd_event                          
 5625 root      16   0  2152 1188  644 S    0  0.1   0:00.00 acpid                                  
 5766 root      17   0  1680  496  412 S    0  0.0   0:00.61 dd                                     
 5768 klog      18   0  2408 1336  388 S    0  0.1   0:00.44 klogd                                  
 5793 hplip     15   0 12872  924  696 S    0  0.1   0:00.00 hpiod                                  
 5796 hplip     15   0  9408 4672 1092 S    0  0.5   0:00.01 python                                 
 5872 messageb  17   0  2196  824  672 S    0  0.1   0:00.07 dbus-daemon                            
 5887 haldaemo  16   0  6864 5436 1536 S    0  0.5   0:01.83 hald                                   
 5888 root      16   0  2720  980  836 S    0  0.1   0:00.06 hald-runner                            
 5893 haldaemo  17   0  2004  792  696 S    0  0.1   0:00.00 hald-addon-acpi                        
 5943 haldaemo  15   0  2004  792  692 S    0  0.1   0:00.19 hald-addon-keyb                        
 5954 haldaemo  16   0  2012  820  716 D    0  0.1   0:00.38 hald-addon-stor                        
 5955 haldaemo  16   0  2008  820  716 D    0  0.1   0:00.90 hald-addon-stor                        
 5957 haldaemo  16   0  2012  820  716 S    0  0.1   0:00.06 hald-addon-stor                        
 5958 haldaemo  16   0  2012  820  716 S    0  0.1   0:00.11 hald-addon-stor                        
 6001 Debian-e  16   0  5200  940  680 S    0  0.1   0:00.00 exim4                                  
 6056 root      24   0  4764 1032  732 S    0  0.1   0:00.00 sshd                                   
 6102 ntp       16   0  3588 3588 2892 S    0  0.3   0:00.31 ntpd                                   
 6118 root      21   0  1972  712  616 S    0  0.1   0:00.00 hcid                                   
 6125 root      21   0  1620  460  384 S    0  0.0   0:00.00 sdpd                                   
 6138 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd                               
 6152 root      16   0  1624  296  232 S    0  0.0   0:00.00 mdadm                                  
 6171 daemon    16   0  1800  392  296 S    0  0.0   0:00.00 atd                                    
 6177 root      16   0  2328  656  532 S    0  0.1   0:00.25 fcron                                  
 6513 root      16   0  2744  632  504 S    0  0.1   0:00.00 kdm                                    
 6561 root      16   0  3676 1356 1088 S    0  0.1   0:00.00 kdm                                    
 6568 root      16   0  1560  492  424 S    0  0.0   0:00.00 getty                                  
 6570 root      16   0  1564  492  424 S    0  0.0   0:00.00 getty                                  
 6572 root      16   0  1560  492  424 S    0  0.0   0:00.00 getty                                  
 6574 root      16   0  1564  496  424 S    0  0.0   0:00.00 getty                                  
 6575 root      16   0  1560  488  424 S    0  0.0   0:00.00 getty                                  
 6576 root      16   0  1564  496  424 S    0  0.0   0:00.00 getty                                  
 6577 root      16   0   116   24   12 S    0  0.0   0:00.00 runsvdir                               
 6596 hippo     17   0  2924 1412  956 S    0  0.1   0:00.08 x-session-manag                        
 6631 hippo     16   0  4328  732  472 S    0  0.1   0:00.00 ssh-agent                              
 6634 hippo     16   0  2712  648  520 S    0  0.1   0:00.00 dbus-launch                            
 6635 hippo     18   0  2080  420  324 S    0  0.0   0:00.00 dbus-daemon                            
 6663 hippo     16   0 23488 3452 2024 S    0  0.3   0:00.18 kdeinit                                
 6666 hippo     16   0 23216 2748 1576 S    0  0.3   0:00.06 dcopserver                             
```

---

### Post by HippoMan on 2006-07-03
P.S. -- This is the result of **uname -rv** on the systems for which this problem is occurring:

2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 200

---

### Post by HippoMan on 2006-07-05
I'm bumping this thread.  Does anyone know what could be causing me to have such an excessive load average?

Thanks.

---

### Post by HippoMan on 2006-07-05
Until now, I had overlooked the following report, which seems to pertain to this bug (yes, after reading the referenced discussion, I believe that it is indeed a bug):

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557")

---

