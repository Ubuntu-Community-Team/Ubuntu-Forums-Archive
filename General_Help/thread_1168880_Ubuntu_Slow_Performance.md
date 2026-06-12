---
title: "Ubuntu Slow Performance"
date: 2009-05-24
forum: General Help
---

### Post by ericdintzis on 2009-05-24
I'm a new user and really looking forward to using Linux. I've got a Dell Latitude Intel Pentium 1.6 GHz                      with 1gb RAM.
I've just installed Ubuntu 9.04 and I am finding the system extremely slow.
The slowness is most noticable when browsing in Firefox and just scrolling down a page. It is extremely frustrating.

I have read some forum articles, but havent seen any useful advise. My expectation was that ubuntu would be screaming on this platform.

Any advice would  be appeciated.

Here is output from Top.

Cpu(s): 36.1%us,  2.3%sy,  0.0%ni, 61.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1026412k total,   501964k used,   524448k free,    19528k buffers
Swap:  1646620k total,        0k used,  1646620k free,   192772k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3444 edintzis  20   0  301m 112m  31m R 19.9 11.3   3:25.24 firefox            
 2587 root      20   0  154m  49m 8872 S 17.2  4.9  13:35.59 Xorg               
 3239 edintzis  20   0 36204  19m  13m S  0.7  1.9   0:03.92 gnome-panel        
 4052 edintzis  20   0 33612  14m 9272 S  0.7  1.4   0:03.31 gnome-terminal     
 4098 edintzis  20   0  2448 1180  912 R  0.3  0.1   0:06.24 top                
    1 root      20   0  3084 1884  564 S  0.0  0.2   0:01.58 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify

---

### Post by Super TWiT on 2009-05-24
For me, installing the proprietary video driver helped a lot.  To install it, go into the System menu, Administration, and Hardware drivers.  It may allow you to install a proprietary driver for added performance.  Also, creating a swap partition (virtual memory in windows) may help too.  I also am on a Pentium 4 and am experiencing good performance.

---

