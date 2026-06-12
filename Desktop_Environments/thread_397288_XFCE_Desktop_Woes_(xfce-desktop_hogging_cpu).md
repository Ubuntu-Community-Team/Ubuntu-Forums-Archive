---
title: "XFCE Desktop Woes (xfce-desktop hogging cpu)"
date: 2007-03-30
forum: Desktop Environments
---

### Post by scottbot84 on 2007-03-30
Right now I'm running Xubuntu Feisty on my 750mhx PIII 380MB RAM vaio laptop. This problem was also present in Dapper AND Edgy for me. A fresh install of Xubuntu runs great, but eventually xfdesktop will start up and max out my cpu to almost 100%. I can't kill it without spawning another one, the "Let XFCE manage my desktop" option in xfce-setting-show does nothing. ALso my panel menu will not apear. Eventually after about 15-20 mins everything works fine again, but obviously for a laptop I don't want to wait that long for my system to be usable. As is it is nearly unusable. I have not installed anything outside of the ubuntu repositories. I don't have any other huge memory intensive processes. the xfce menu plugin also causes the same problems. if it helps any here are my processess from top 
>  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                           PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                           
 7074 scott     25   0 44112  16m 6960 R 75.9  4.3   5:33.26 xfdesktop                                                         
 6844 root      15   0  150m  15m 6548 S 11.2  4.2   1:04.03 Xorg                                                              
 7171 scott     15   0  148m  49m  19m S  9.6 13.3   1:21.36 swiftfox-bin                                                      
 7082 scott     15   0 56364  12m 7688 S  1.3  3.3   0:03.47 tilda                                                             
 5420 haldaemo  15   0  9952 8320 1712 S  0.5  2.2   0:08.53 hald                                                              
 5775 root      15   0  4632 1856 1476 S  0.4  0.5   0:04.37 powersaved                                                        
 5397 messageb  15   0  2848 1056  736 S  0.2  0.3   0:07.50 dbus-daemon                                                       
 7069 scott     15   0 17036 9.8m 6632 S  0.2  2.6   0:05.00 xfwm4                                                             
    5 root      10  -5     0    0    0 S  0.1  0.0   0:00.12 events/0                                                          
 7058 scott     15   0 43408 5816 4436 S  0.1  1.5   0:01.12 xfce4-session                                                     
 7064 scott     15   0 43048  13m 8196 S  0.1  3.5   0:12.39 xfce-mcs-manage                                                   
 7075 scott     15   0 42596 9616 6980 S  0.1  2.5   0:02.92 xfce4-panel                                                       
    1 root      18   0  1744  808  584 S  0.0  0.2   0:02.68 init                                                              
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                       
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                       
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                        
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                                           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                                           
   30 root      12  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                         
   31 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                            
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                      
  115 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod                                                           
  134 root      16   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                           
  135 root      15   0     0    0    0 S  0.0  0.0   0:00.18 pdflush                                                           
  136 root      10  -5     0    0    0 S  0.0  0.0   0:00.37 kswapd0                                                           
  137 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                             
 1916 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                     
 1917 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                             
 1936 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                          
 1953 root      10  -5     0    0    0 S  0.0  0.0   0:00.37 ata/0                                                             
 1954 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                           
 1956 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                       
 1972 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                         
 1973 root      10  -5     0    0    0 S  0.0  0.0   0:00.67 scsi_eh_1                                     
 7074 scott     25   0 44112  16m 6960 R 75.9  4.3   5:33.26 xfdesktop                                                         
 6844 root      15   0  150m  15m 6548 S 11.2  4.2   1:04.03 Xorg                                                              
 7171 scott     15   0  148m  49m  19m S  9.6 13.3   1:21.36 swiftfox-bin                                                      
 7082 scott     15   0 56364  12m 7688 S  1.3  3.3   0:03.47 tilda                                                             
 5420 haldaemo  15   0  9952 8320 1712 S  0.5  2.2   0:08.53 hald                                                              
 5775 root      15   0  4632 1856 1476 S  0.4  0.5   0:04.37 powersaved                                                        
 5397 messageb  15   0  2848 1056  736 S  0.2  0.3   0:07.50 dbus-daemon                                                       
 7069 scott     15   0 17036 9.8m 6632 S  0.2  2.6   0:05.00 xfwm4                                                             
    5 root      10  -5     0    0    0 S  0.1  0.0   0:00.12 events/0                                                          
 7058 scott     15   0 43408 5816 4436 S  0.1  1.5   0:01.12 xfce4-session                                                     
 7064 scott     15   0 43048  13m 8196 S  0.1  3.5   0:12.39 xfce-mcs-manage                                                   
 7075 scott     15   0 42596 9616 6980 S  0.1  2.5   0:02.92 xfce4-panel                                                       
    1 root      18   0  1744  808  584 S  0.0  0.2   0:02.68 init                                                              
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                       
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                       
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                        
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                                           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                                           
   30 root      12  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                         
   31 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                            
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                      
  115 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod                                                           
  134 root      16   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                           
  135 root      15   0     0    0    0 S  0.0  0.0   0:00.18 pdflush                                                           
  136 root      10  -5     0    0    0 S  0.0  0.0   0:00.37 kswapd0                                                           
  137 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                             
 1916 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                     
 1917 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                             
 1936 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                          
 1953 root      10  -5     0    0    0 S  0.0  0.0   0:00.37 ata/0                                                             
 1954 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                           
 1956 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                       
 1972 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                         
 1973 root      10  -5     0    0    0 S  0.0  0.0   0:00.67 scsi_eh_1    

---

