---
title: "slowness on asus A6VC"
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by cingo_5 on 2007-05-09
Hi,

Frist of all, sorry for my approximate english, i hope you can understand my problem however
i have a notebook Asus A6vc (intel centrino 1,7 Ghz; 1,5 Gb Ram, nvidia 6200 TC) with installed Ubuntu Fiesty Fawn 7.04. it works great!
I wanted to try AIGLX+Beryl so I had modified xorg.conf doing this:
```

$: sudo nvidia-xconfig --composite
$: sudo nvidia-xconfig --render-accel
$: sudo nvidia-xconfig --allow-glx-with-composite
$: sudo nvidia-xconfig --add-argb-glx-visuals
```

then I installed gnome-compiz-manager, i restarted my notebook and I launched compiz.
the effect and the cube was ok but they don't worked good, they was quite slow. 
In this moment i was plugged at the electric line, so I tried to disconnect the the notebook from electic line
and AIGLX with compiz go very well...!

this is my "top" when the note is plugged at the electric line
```
top - 21:25:21 up 10 min,  2 users,  load average: 0.08, 0.25, 0.18
Tasks: 102 total,   3 running,  98 sleeping,   0 stopped,   1 zombie
Cpu(s): 34.8%us, 17.4%sy,  0.0%ni, 34.8%id,  0.0%wa,  6.5%hi,  6.5%si,  0.0%st
Mem:   1555772k total,   472532k used,  1083240k free,    56224k buffers
Swap:  2441840k total,        0k used,  2441840k free,   241596k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4922 root      15   0 50856  28m 8268 R  4.3  1.9   0:20.39 Xorg               
 5366 cingo     15   0 31504  18m 7468 S  2.0  1.2   0:04.54 compiz.real        
 5537 cingo     15   0  155m  43m  20m S  1.3  2.8   0:11.41 firefox-bin        
 2010 root      10  -5     0    0    0 S  0.3  0.0   0:00.10 ata/0              
 5947 cingo     15   0 59484  16m  10m R  0.3  1.1   0:00.38 gnome-terminal     
    1 root      15   0  2912 1848  524 S  0.0  0.1   0:02.01 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   31 root      15  -5     0    0    0 S  0.0  0.0   0:00.15 kacpid             
   32 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kacpi_notify       
  151 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod            
  172 root      16   0     0    0    0 S  0.0  0.0   0:00.00 pdflush 
```

I can't see nothing strange... what it can be? :confused: 
previously I had installed Dapper with beryl and Xgl, and they always worked good ...
Sorry again for my Italish.. :)  Thanks

---

