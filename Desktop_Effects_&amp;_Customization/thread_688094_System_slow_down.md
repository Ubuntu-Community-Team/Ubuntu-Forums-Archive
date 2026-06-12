---
title: "System slow down"
date: 2008-02-05
forum: Desktop Effects &amp; Customization
---

### Post by bargi on 2008-02-05
Hi ,

I am facing the problem of system slow........

I have changed the appearance from System -> Preference->Appearance.

After that my system slows down, so I changed it back to none and restart my PC.

But the problem was same...........

I am pasting the output of top command:

```

top - 11:58:21 up  1:27,  2 users,  load average: 0.06, 0.20, 0.13
Tasks: 123 total,   1 running, 122 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.8%us,  1.0%sy,  0.0%ni, 90.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1002940k total,   725176k used,   277764k free,    84244k buffers
Swap:  1052216k total,        0k used,  1052216k free,   368524k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 5004 root      15   0 75224  19m 4424 S   14  2.0   3:13.34 Xorg                                                            
 5390 AAA   15   0  183m  75m  21m S    3  7.7   2:07.12 firefox-bin                                                     
 5211 AAA   15   0 33572  25m 7252 S    2  2.6   1:08.90 Xgl                                                             
 5409 AAA   15   0 78748  40m  27m S    0  4.1   0:15.72 kdevelop                                                        
 6138 AAA   15   0  2368 1168  876 R    0  0.1   0:00.01 top                                                             
    1 root      18   0  2948 1852  532 S    0  0.2   0:01.53 init                                                            
    2 root      12  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                     
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                     
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                      
    9 root      10  -5     0    0    0 S    0  0.0   0:00.02 events/0                                                        
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                        
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                         
   31 root      14  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                       
   32 root      20  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                       
   33 root      11  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                          
   34 root      12  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                    
  117 root      20  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                         
  142 root      16   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                         
  143 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                         
  144 root      13  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                         
  195 root      13  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                           
  196 root      14  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                           
 2044 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                   
 2045 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                           
 2098 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                           
 2099 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                           
 2100 root      13  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                         
 2150 root      12  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                       



```   

Can anybody help in solving the problem. I am using ubuntu 7.1
Thanks

---

### Post by Sam Lars on 2008-02-27
Slow in what way?  Nothing there really stands out...

---

