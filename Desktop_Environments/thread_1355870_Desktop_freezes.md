---
title: "Desktop freezes"
date: 2009-12-15
forum: Desktop Environments
---

### Post by ashwinrao on 2009-12-15
Hello there,

My desktop often freezes when I access web using Firefox or watching nay movies. It freezes for seconds and resumes. I am using Ubuntu 9.10 Karmic with comfiz and Nvidia drivers. I can provide more information regarding this issue. Please any body help! I am using AMD 64 with Nvidia 6100 driver. I am total newbie with Linux but I can perform the suggested operations. I have followed most of the remedies suggested in this forum but without any luck. 

This is the output for top command using terminal: 
Tasks: 152 total,   3 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.0%us,  6.0%sy,  0.0%ni, 85.8%id,  0.0%wa,  1.0%hi,  0.3%si,  0.0%st
Mem:    958376k total,   944260k used,    14116k free,    41384k buffers
Swap:  2000052k total,    33436k used,  1966616k free,   305360k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1497 root      20   0  211m  91m  19m R  5.6  9.7   8:46.74 Xorg               
18738 ashwinra  20   0  296m  18m  10m S  3.3  2.0   0:01.27 gnome-terminal     
 2075 ashwinra  20   0  596m  65m  29m R  1.0  7.0   2:12.62 cairo-dock         
 2063 ashwinra  20   0  323m  64m  18m S  0.7  6.9   6:33.70 compiz.real        
 2155 ashwinra  20   0  114m  26m 4400 S  0.7  2.9   0:35.87 ubuntuone-syncd    
 1292 root      20   0 74896 3144 2856 S  0.3  0.3   0:00.75 gdm-binary         
 1992 ashwinra  20   0  203m  16m 9524 S  0.3  1.7   0:02.07 notify-osd         
 2069 ashwinra  20   0  284m  18m 9492 S  0.3  2.0   0:10.76 emerald            
 2070 ashwinra  20   0  583m  37m  20m S  0.3  4.0   0:22.10 nautilus           
18765 ashwinra  20   0 19132 1348  980 R  0.3  0.1   0:00.14 top                
    1 root      20   0 19320 1632 1160 S  0.0  0.2   0:00.72 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset 

Please help me, I'm lost...:(

---

